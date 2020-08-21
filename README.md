# Data Modeling with Postgres (Sparkify)

This project creates a database schema and ETL pipeline for the purpose of analyzing song data and user activity from a music streaming app.

Uses a python script to extract data - in JSON fomatted files and stored in local direcgtories - and load them into a Postgresql database designed using the star schema for query optimization.

Song data comes from the [Million Song DataSet](http://millionsongdataset.com/).
Log Data comes from the Sparkify App user data.

### Data model:
Postgres tables are modeled using a star schema for query optimization. A single fact table, Songplays, and is surrounded by four dimension table branches.

#### Schema for Song Play Analysis
##### Fact Table
1. songplays - records in log data associated with song plays i.e. records with page NextSong
- songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
##### Dimension Tables
1. users - users in the app
 - user_id, first_name, last_name, gender, level
2. songs - songs in music database
- song_id, title, artist_id, year, duration
3. artists - artists in music database
- artist_id, name, location, latitude, longitude
4. time - timestamps of records in songplays broken down into specific units
- start_time, hour, day, week, month, year, weekday

### Files:
##### scripts for running project:
1. create_tables.py drops and creates your tables.
2. sql_queries.py contains all create, drop, and insert sql queries.
3. etl.py reads and processes files from song_data and log_data and loads them into your tables.

##### notebooks for development and testing:
4. etl.ipynb reads and processes a single file from song_data and log_data and loads the data into tables. Used for developing and testing the ETL process for each of the tables that is used in etl.py.
5. test.ipynb displays the first few rows of each table to let you check your database.

### How to run:
Run create_tables.py to create all the Postgres tables.
Run etl.py to load data from the log and song files into the Postgres tables.
Sample queries and data verification can be found in the test.ipynb notebook.
