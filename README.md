# Data Engineering with AWS: Project Cloud Data Warehouse

## Purpose
I am a Data Engineer for a startup called Sparkify. Sparkify's is rapidly scaling their user base and song data base to service these new users. To accomodate this, we are moving their data into the cloud. As part of this process, I have been tasked with creating an ETL pipeline to move data from an S3 AWS bucket, stage it in Reshift, and transofrm it into tables for analytical purposes.


## Database Schema and ETL Pipeline Design

### Database Schema
I am going to create two staging tables:

> staging_events: will source from JSON logs and contain dimenionson users 
    - artist
    - auth
    - firstName
    - gender
    - itemInSession
    - lastName
    - length
    - level
    - location
    - method
    - page
    - registration
    - sessionId
    - song
    - status
    - ts
    - userAgent
    - userId
    
 > staging_songs: will source from JSON logs and contain dimenionson songs 
     - num_songs
     - artist_latitude
     - artist_longitude
     - artist_location
     - artist_name
     - song_id
     - title
     - year
     - duration
     - artist_id
     
I will also create a fact table.

> songplays: data about song plays
    - songplay_id (PK)
    - start_time
    - user_id
    - level
    - song_id
    - artist_id
    - session_id
    - duration
    - user_agent

Finally, the database will have four dimension tables.

> users: data on users
    - user_id (PK)
    - first_name
    - last_name
    - gender
    - level
    
 > songs: data on the songs in database
     - song_id (PK)
     - title
     - artist_id
     - year
     - duration
     
> artist: data on artists in data
    - artist_id (PK)
    - name
    - location
    - latitude
    - longitude
    
 > time: data on when songs were played
     - start_time (PK)
     - hour
     - day
     - week
     - month
     - year
     - weekday
     
     
### ETL
etl.py will load data from S3 to the staging tables and then to the analytical tables.