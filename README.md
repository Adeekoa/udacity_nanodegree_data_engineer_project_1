# **Sparkify**
This is a data modelling project using PostgreSQL database for storage and python to build an ETL pipeline
## **Description**
Sparkify is a tech startup which just developed a music streaming app and the company is interestd in analyzing the data on songs and users activity they have have been collecting on the app. Currently, querying the data which resides in a directory of JSON logs is challenging for the company. 

This project is aimed at solving the problem by creating a repository for the data using Postgres Database, designing the database schema for optimal query performance, and building an ETL pipeline for ingesting data from different sources and loading data into the database in preparation for analysis.

## **Dataset**
Two datasets are utilized in this project i.e. *songs* and *logs*. The datasets are files in JSON format. The *songs* dataset contains details about songs and their associated artists. 

Below is what a song file looks like:
```
{
    "num_songs": 1, 
    "artist_id": "ARJIE2Y1187B994AB7", 
    "artist_latitude": null, 
    "artist_longitude": null, 
    "artist_location": "", 
    "artist_name": "Line Renaud", 
    "song_id": "SOUPIRU12A6D4FA1E1", 
    "title": "Der Kleine Dompfaff", 
    "duration": 152.92036, 
    "year": 0
}
```
The *log* dataset on the hand consist of files that contain activity logs of songs contained in the *songs* dataset.

## **Running the Python Scripts**
It is important to follow the steps below in running the python scripts in this project.

1. Run  ```create_tables.py``` to create the database.
2. Next, run ```sql_queries.py``` to create the tables and initialize the sql queries
3. Run the ```etl.ipynb``` file to populate the tables in the database with just 1 data at a time.
4. Finally, run ```etl.py``` to insert all the records from the two repositories into the tables in the database.
5. You can run ```test.ipynb``` to confirm the scripts worked perfectly as intended.

***Note***: *you will have to restart the kernel each time you run the ```etl.ipynb``` or  ```test.ipynb``` to close the connection to the datase, else ```create_tables.py``` and ```etl.py``` will not run*

## **Understanding the Files**

* ```create_tables.py``` drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
* ```test.ipynb``` displays the first few rows of each table to let you check your database.
* ```etl.py``` reads and processes files from ```song_data``` and ```log_data``` and loads them into your tables. You can fill this out based on your work in the ETL notebook.
* ```etl.ipynb``` reads and processes a single file from ```song_data``` and ```log_data``` and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
* ```sql_queries.py``` contains all the sql queries, and is imported into ```create_tables.py```, ```etl.py``` and ```etl.ipynb```.

## **Database Schema and ETL**
For this project, the star schema (as seen below) is utilized to model the data and it is preferred based on the following reasons:

1. It is simple to understand and build
2. It eliminates the need for complex joins when querying data from the database.
3. It optimizes storage and query efficiency.

![](Capture.PNG)

For the *ETL* process, tables are created in line with the schema design. Running the ```etl.py``` script populates the tables from the ```songs``` and ```log``` datasets

