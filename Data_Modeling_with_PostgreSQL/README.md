## Introduction

Sparkify is a startup which wants to analyze their data on their new music streaming app. The goal of the project is to build a PostgreSQL database and an ETL pipeline using python to load the data into the database for Sparkify. The database will help the analytics team of Sparkify understand what songs their users are listening to and provide them with some more insights. 

In the first step, we understand the data at hand and move on to create the database schema. The next step is to create the tables in the database using the defined database schema. After that, an ETL pipeline needs to be created to load the data into respective tables of the database.    

## Dataset Description:
There are two datasets: 
1) The Song dataset: JSON files consisting of song data from Million Song Dataset 
2) The Log  dataset: JSON files consisting of data generated from the Event Simulator

## Database Schema Design and ETL pipeline

The database schema follows a star schema for the database design. The star schema is more apt for this scenario considering the type of analysis we want to do. 

The database schema is as follows:

**Fact Table**

1) **songplays** - records in log data associated with song plays i.e. records with page NextSong
    - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

**Dimension Tables**

1) **users** - users in the app
    - user_id, first_name, last_name, gender, level

2) **songs** - songs in music database
    - song_id, title, artist_id, year, duration

3) **artists** - artists in music database
    - artist_id, name, location, latitude, longitude

4) **time** - timestamps of records in songplays broken down into specific units
    - start_time, hour, day, week, month, year, weekday


The ETL pipeline consist of three functions. The first function is a driver to process the data in the files. It call the appropriate fuctions to process the data based on the type of files. As mentioned above, there are two types of files, namely the song data and the log dataset. The other functions are precisely for that purpose, i.e to process the song data and log data respectively.  


## Steps to run the Code in terminal
##### Run the following commands in order:
1)python create_tables.py
2)python etl.py

## Explaination of the files:

**create_tables.py -** This file creates a connection to the Sparkify Database

**sql_queries.py -** This file has a queries to create tables, Insert data and drop tables

**etl.py -** This file is an ETL pipline which processes the song & log file to load them into the database   

**etl.ipynb -** Notebook to test queries to create the etl.py file

**test.ipynb -** Notebook to test the database