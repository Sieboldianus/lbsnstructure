# User Privacy & Anonymization

While complete anonymization will result in data that is difficult to use, there are a number of techniques that ensure user privacy and still allow researchers to analyize data.
Firstly, there are two options available for anonymizing personal user information, `encrypt` and `digest`.

## Encrypt Function

**Encrypt** will *encrypt* content based on a specific password. Decrypt can be used to get the original content with the password.
The Encrypt Function is useful when storing values in the database. While this is not implemented at the moment, it is planned as a feature in the future. You can also use encrypt to share data with colleagues: the same content will always encrypt to the same string. This means, even without having the password, data is useful for counting unique occurrences.
```sql
SELECT encode(encrypt(user_guid::bytea, 'key'::bytea, 'aes'), 'hex') AS "user_GuidCrypt";
```

```sql
SELECT decrypt(decode(user_guid::hex,'bytea'), 'key'::bytea, 'aes') AS "user_guid;
```

## Digest/Hash Function

```sql
SELECT encode(digest('yoursalt' || 'yoursaltpw'|| user_guid,'sha256'), 'hex') AS "user_GuidHash";
```

Unlike encrypt, **digest** will *hash* content by using a hashing-function such as `sha256`. This cannot be reversed - in other words, once content is hashed, its original content cannot be recovered. `Sha256` is, currently said, 100% secure.
Hashing can be applied to disguise original data such as user_guids, photo_guids etc. where we only need to know that values are unique. A given user_guid, for example, will always result in the same hash. Different user_guids will always have different hashes.
The `salt` and `password` used when Hashing increase security, as they will add another layer of security (simply appended to original string), which prevents compromised hashes [from other user's mistakes](https://security.stackexchange.com/questions/51959/why-are-salted-hashes-more-secure-for-password-storage). They are simply two unique strings (that shouldn't be shared).
The Digest/Hash Function is useful when sharing data with external partners, where it is not important to know the original user-id.

## Which one should I chose?  
If you are unsure, use encryption, as it combines advantages of both and still gives you the ability to decrypt content in specific cases. If you're sharing data online publicly, hashing is the more secure alternative, as it is nearly impossible to un-hash content (at least not within a reasonable amount of time) - even if someone managed to get the `salt` and `pw` you used. Sometimes, it is not necessary to encrypt/hash all data. For example, if a tag is used by hundreds or thousands of users in a single shared dataset, it seems possible to leave it in clear text. On the other hand, if a specific tag is only by a single user, it is recommended to hash or encrypt this tag. A researcher may still be able to use it to count unique terms, but the term itself cannot be used anymore to discover the original user.

## Example Usage
The following code will export a CSV to local drive E: and encode/hash user_guids and photo_guids:

```sql
COPY
(SELECT t1.origin_id,
 		--t1.post_guid, --the original post_guid
 		--encode(digest('yoursalt' || 'yourpw'|| t1.post_guid,'sha256'), 'hex') AS "post_guid", --the hashed post_guid
 		encode(encrypt(t1.post_guid::bytea, 'yourpw'::bytea, 'aes'), 'hex') AS "post_guid", --the encrypted post_guid
 		ST_Y(t1.post_latlng) As "latitude", 
 		ST_X(t1.post_latlng) As "longitude",
 		t1.place_guid,
 		t1.city_guid,
 		t1.country_guid,
 		--t1.user_guid, --the original user_guid
 		--encode(digest('yoursalt' || 'yourpw'|| t1.user_guid,'sha256'), 'hex') AS "user_guid", --the hashed user_guid
		encode(encrypt(t1.user_guid::bytea, 'yourpw'::bytea, 'aes'), 'hex') AS "user_guid", --the encrypted user_guid
 		t1.post_publish_date,
 		t1.post_body,
 		t1.post_geoaccuracy,
 		t1.hashtags,
 		t1.smilies As "emojis",
 		t1.post_like_count,
 		t1.post_comment_count,
 		t1.post_title,
 		t1.post_create_date,
 		t1.post_thumbnail_url,
 		t1.post_url,
 		t1.post_type,
 		t1.post_filter,
 		t2.name,
 		t2.city_guid,
 		t2.post_count as "place_post_count"
FROM   public.post t1
FULL OUTER Join public.place t2 on t1.place_guid=t2.place_guid
WHERE  t1.post_latlng 
    && -- intersects
    ST_MakeEnvelope (
        -78.5311317443848, 38.0075251589045, --lng-lat bounding 
        -78.4281349182129, 38.0493752876317, --lng-lat box limits (Charlottesville Center)
        4326)
)
TO '/Charlottesville_Enc.csv' --will be stored in E
WITH (format CSV, DELIMITER ',', encoding 'UTF-8', quote '"', escape '"', header);
    
```