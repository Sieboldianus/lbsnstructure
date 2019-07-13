# Spatial Queries

An extensive List of example queries can be found [here](Queries/queries)

**Description:** A Standard BBox query on post-table
```sql
SELECT *
FROM   public.post
WHERE  post_latlng 
    --&& -- intersects,  gets more rows  -- CHOOSE ONLY THE
    @ -- contained by, gets fewer rows -- ONE YOU NEED!
    ST_MakeEnvelope (
        13.3896732330322, 52.5135569954247, -- bounding 
        13.4120750427246, 52.5221225855114, -- box limits (Berlin)
        4326)
LIMIT 100; --optional
```
**Description:** Sometimes, it is necessary to retrieve Lat/Lng coordinates and not the Well-Known Text (WKT) representation. The following query will output ST_Y and ST_X column with lat/lng coordinates for post_latlng column.
```sql
SELECT origin_id,post_guid,ST_Y(post_latlng), ST_X(post_latlng),place_guid,city_guid,country_guid,user_guid,post_publish_date,post_body,post_geoaccuracy,hashtags,smilies,post_like_count,post_comment_count,post_title,post_create_date,post_thumbnail_url,post_url,post_type,post_filter
FROM   public.post
WHERE  origin_id = 1 AND post_latlng 
    @
    ST_MakeEnvelope (
        13.3896732330322, 52.5135569954247, -- bounding 
        13.4120750427246, 52.5221225855114, -- box limits (Berlin)
        4326)
```

**Description:** Example query for Germany bounding box with thematic selection of places that contain either "park" or "garden" in name.
```sql
SELECT *
FROM  public.place p2
WHERE p2.origin_id = 1 AND LOWER(p2.name) SIMILAR TO LOWER('%park%|%garten%')
AND p2.geom_center
    &&
    ST_MakeEnvelope (
        5.98865807458, 47.3024876979, -- bounding 
        15.0169958839, 54.983104153, -- box limits (Germany)
        4326);
```

# Select Distinct, Estimation, Sum & Count Unique

**Description:** This (very expensive) query will count unique posts that have no geo-coordinates and group the corresponding place_guids based on occurrence. This list can then be used to retrieve geo-coordinates, beginning with the most frequent missing locations.
```sql
SELECT 
	COUNT(DISTINCT(p1.place_guid)) AS Placecount,
	p1.place_guid
FROM public.post p1
WHERE (
   SELECT geom_center
   FROM   public.place p2
   WHERE  (p1.origin_id,p1.place_guid) IN (VALUES(1, p2.place_guid))
   ) IS NULL
GROUP BY
    p1.place_guid
ORDER BY Placecount DESC;
```

**Description:** the following query selects all posts for the area of Dresden and counts the number of emojis by unnesting emoji-array column and summing up distinct entries.
```sql
SELECT SUM((SELECT COUNT(s) FROM UNNEST(smilies) s)) as total_emojis
FROM   public.post
WHERE origin_id = 1
AND  post_latlng 
    @
    ST_MakeEnvelope (
        13.5818481445313, 50.9722648893675, -- bounding 
        13.88671875, 51.1380014880626, -- box limits (Dresden)
        4326)
```

**Description:** The following query makes use of the stats_collector and autovacuum daemon (see explanation [here](https://www.citusdata.com/blog/2016/10/12/count-performance/)) by estimating counts (much faster than exact counts). Any query can be substituted. Prior to execution, make sure `count_estimate` function is available in the LBSN-DB.
```sql
SELECT count_estimate('SELECT 1 FROM public.post WHERE origin_id = 1 AND post_latlng IS NULL');
```

**Description:** Another example of fast total count estimation is using the pg_class reltuples.
```sql
SELECT reltuples::bigint AS estimate FROM pg_class where relname='city';
```



# Database Structure, Maintenance & Indexes

**Description:** The following query will list all available indexes in LBSN-DB.
```sql
SELECT i.relname as indname,
       i.relowner as indowner,
       idx.indrelid::regclass,
       am.amname as indam,
       idx.indkey,
       ARRAY(
       SELECT pg_get_indexdef(idx.indexrelid, k + 1, true)
       FROM generate_subscripts(idx.indkey, 1) as k
       ORDER BY k
       ) as indkey_names,
       idx.indexprs IS NOT NULL as indexprs,
       idx.indpred IS NOT NULL as indpred
FROM   pg_index as idx
JOIN   pg_class as i
ON     i.oid = idx.indexrelid
JOIN   pg_am as am
ON     i.relam = am.oid;
```

**Description:** This query will drop all inactive connections that haven't responded since 5 Minutes. Sometimes, queries to the DB are not shut down correctly by scripts (due to network error or other problems). These may remain open and block other connections.
```sql
WITH inactive_connections AS (
    --see https://stackoverflow.com/questions/12391174/how-to-close-idle-connections-in-postgresql-automatically
    SELECT
        pid,
        rank() over (partition by client_addr order by backend_start ASC) as rank
    FROM 
        pg_stat_activity
    WHERE
        -- Exclude the thread owned connection (ie no auto-kill)
        pid <> pg_backend_pid( )
    AND
        -- Exclude known applications connections
        application_name !~ '(?:psql)|(?:pgAdmin.+)'
    AND
        -- Include connections to the same database the thread is connected to
        datname = current_database() 
    AND
        -- Include connections using the same thread username connection
        usename = current_user 
    AND
        -- Include inactive connections only
        state in ('idle', 'idle in transaction', 'idle in transaction (aborted)', 'disabled') 
    AND
        -- Include old connections (found with the state_change field)
        current_timestamp - state_change > interval '5 minutes' 
)
SELECT
    pg_terminate_backend(pid)
FROM
    inactive_connections 
WHERE
    rank > 1 -- Leave one connection for each application connected to the database
```