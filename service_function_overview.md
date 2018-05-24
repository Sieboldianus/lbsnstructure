### Symbols: Origin of individual Data aspects across services

⚫ = Not Available
⍜ = User Contributed/ Input Device or Service Measure
⍉ = Service Generated/ From Service
⌽ = Analyst Algorithm Derived (Version Number)
    ⌽⥉ = Substituted from other internal data (e.g. other table, other column, higher granularity information substitution)
    ⌽⥈ = Substituted from other external data (e.g. other service, data source etc.)
    ⌽⨮ = Summarized
    ⌽⌽ = Empty Information Supplemented
    ⌽◑ = Value Mapping (see Proto Buffers enum lists)
⨷ = Analyst Defined

() = Value

### Origin

|    | INSTAGRAM   | FLICKR   | TWITTER   | FACEBOOK   | FOURSQUARE  |
|:-:|:-:|:-:|:-:|:-:|:-:|
| origin_id  | (1) ⨷   | (2) ⨷   | (3) ⨷   | (4) ⨷   | (5) ⨷  |
| name  | ⍉   | ⍉   | ⍉   | ⍉   | ⍉  |

### Post

|    | INSTAGRAM   | FLICKR   | TWITTER   | FACEBOOK   | FOURSQUARE  |
|:-:|:-:|:-:|:-:|:-:|:-:|
| post_latlng   | ⚫  | ⍜  | ⍜  | ⚫  | ⚫  |
| place  | ⍜  | ⍉  | ⍉  | ⍜  | ⍜  |
| city   |  ⍉ | ⚫  | ⍉  | ⍉  | ⍉  |
| country  | ⍉  | ⚫  | ⍉  | ⍉  | ⍉  |
| user   | ⍜  | ⍜  | ⍜  | ⍜  | ⍜  |
| post_publish_date  | ⍜  |   |   |   |   |
| post_body   |   |   |   |   |   |
| PostGeoaccuracy   |   |   |   |   |   |
| hashtags   |   |   |   |   |   |
| emojis    |   |   |   |   |   |
| post_like_count     |   |   |   |   |   |
| post_comment_count     |   |   |   |   |   |
| post_views_count     |   |   |   |   |   |
| post_title    |   |   |   |   |   |
| post_create_date     |   |   |   |   |   |
| post_thumbnail_url     |   |   |   |   |   |
| post_url     |   |   |   |   |   |
| PostType     |   |   |   |   |   |
| post_type     |   |   |   |   |   |
| post_filter     |   |   |   |   |   |
| post_quote_count      |   |   |   |   |   |
| post_share_count      |   |   |   |   |   |
| input_source      |   |   |   |   |   |
| post_language       |   |   |   |   |   |