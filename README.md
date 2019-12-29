# Purpose of the database
`sparkifydb` database is designed to sereve the analytical purpose of the Sparkify startup which specializes in online music streaming. This database should be able to help data analysts at Sparkify to answer essential analytical questions to the business such as:
- What is happenning (which song is played the most now,..)?
- What is the behavior of the customers/users?


# Database schema design and ETL pipeline.
## Database schema
We use STAR schema for our database. The fact table (`songplay`) stores all information of the played songs by users. Other dimension tables (`users`, `time`, `artists`, `songs`) provide some additional information for the fact table. This design is optimized for queries on song play analysis.

* `songplay` (songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent). Table contains all the facts associated with the played songs.
* `users` (user_id, first_name, last_name, gender, level). Table contains users information.
* `songs` (song_id, title, artist_id, year, duration). Table contains all information of a song.
* `artists` (artist_id, name, location, latitude, longitude). Table contains all information of an artirst.
* `time` (start_time, hour, day, week, month, year, weekday). Table provide additional information of the time when the song was played.


## ETL pipeline
The ETL script loops through all the json data files in the `data` directory and extract, process necessay information. Then, it inserts this data into various tables in the `sparkifydb` database.

# Scripts/Notebook explaination
`creat_tables.py`: script to create the database and all the tables. This should be run first.
`sql_queries.py`: stores all SQL queries used in the `create_tables.py` file.
`etl.ipynb`: notebook to prepare `etl.py` script.
`etl.py`: ETL process to transform all raw data files from `data` directory and write to tables in `sparkifydb` database.
`test.ipynb`: notebook to check if we have all the table we want after the running ETL script.




