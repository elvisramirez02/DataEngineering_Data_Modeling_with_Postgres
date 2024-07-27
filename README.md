# 🎵 Data Modeling with Postgres

## Overview

Hey there! 👋

Welcome to my project on **Data Modeling with Postgres**. In this project, I apply data modeling techniques with Postgres and build an **ETL pipeline** using Python. I'm working with a startup that wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. Currently, they are collecting data in JSON format, and the analytics team is particularly interested in understanding what songs users are listening to. 🎶

## Song Dataset

The songs dataset is a subset of the Million Song Dataset. Here are a couple of sample records:

```json
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```

```json
{"artist": null, "auth": "Logged In", "firstName": "Walter", "gender": "M", "itemInSession": 0, "lastName": "Frye", "length": null, "level": "free", "location": "San Francisco-Oakland-Hayward, CA", "method": "GET", "page": "Home", "registration": 1540919166796.0, "sessionId": 38, "song": null, "status": 200, "ts": 1541105830796, "userAgent": "\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"", "userId": "39"}
```

## Schema

To model the data, I've designed a database schema with a **fact table** and several **dimension tables**:

### Fact Table

**songplays** - records in log data associated with song plays (i.e., records with page `NextSong`)

- `songplay_id`
- `start_time`
- `user_id`
- `level`
- `song_id`
- `artist_id`
- `session_id`
- `location`
- `user_agent`

### Dimension Tables

**users** - users in the app

- `user_id`
- `first_name`
- `last_name`
- `gender`
- `level`

**songs** - songs in the music database

- `song_id`
- `title`
- `artist_id`
- `year`
- `duration`

**artists** - artists in the music database

- `artist_id`
- `name`
- `location`
- `latitude`
- `longitude`

**time** - timestamps of records in songplays broken down into specific units

- `start_time`
- `hour`
- `day`
- `week`
- `month`
- `year`
- `weekday`

## Project Files

- **`sql_queries.py`**: Contains SQL queries for dropping and creating fact and dimension tables. Also includes insertion query templates.
- **`create_tables.py`**: Contains code for setting up the database. Running this file creates `sparkifydb` and also creates the fact and dimension tables.
- **`etl.ipynb`**: A Jupyter notebook to analyze the dataset before loading.
- **`etl.py`**: Reads and processes `song_data` and `log_data`.
- **`test.ipynb`**: A notebook to connect to the Postgres database and validate the data loaded.

## How to Run the Python Scripts

To start the ETL pipeline, run the following command:

```bash
python3 etl.py
```

## Conclusion

This project showcases the power of data modeling with Postgres and building an ETL pipeline to enable a music streaming startup to analyze user activity and song data. By creating a well-structured relational database schema, I ensure that the analytics team can easily query and gain insights from the data. 📊

