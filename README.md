# ETL Datasets on Trending YouTube Videos in UK, CA and US
![](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/images/logo.png)

## Background
YouTube maintains a list of the top trending videos on the platform. According to Variety magazine, “To determine the year’s top-trending videos, YouTube uses a combination of factors including measuring users interactions (number of views, shares, comments and likes). Note that they’re not the most-viewed videos overall for the calendar year”. Top performers on the YouTube trending list are music videos (such as the famously virile “Gangam Style”), celebrity and/or reality TV performances, and the random dude-with-a-camera viral videos that YouTube is well-known for.

## Objectives

Data cleanup & analysis and perform ETL on the data as the following: 

* The sources of data that you will extract from.

* The type of transformation needed for this data (cleaning, joining, filtering, aggregating, etc).

* The type of final production database to load the data into (relational or non-relational).

* The final tables or collections that will be used in the production database.

### * **E**xtract
The original datasets were three CSV files with data of several months’ worth of daily trending YouTube videos from the [United States](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/resources/USvideos.csv), [United Kingdom](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/resources/GBvideos.csv) and [Canada](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/resources/CAvideos.csv). All datasets were downloaded from Kaggle at the following link: 
* [Kaggle - Daily statistics for trending YouTube videos](https://www.kaggle.com/datasnaek/youtube-new)

### * **T**ransform
All csv files were first read into a [Jupyter Notebook](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/YouTube_Videos_ETL.ipynb) in their raw forms and new DataFrames were created for each csv using python. The original csv files can be found saved within a folder named resources. In order to start cleaning the data, relevant columns were selected, renamed and added into new filtered DataFrames, with the video_id set as the index for all three data sets. 

### * **L**oad
Data Cleanup & Analysis and SQL Database was chosen due to the similarities within schematic structure of the csvs which is conducive of a relational database. Furthermore, with each dataset having unique IDs, PostgreSQL was used due to the allowance of using primary keys and foreign keys in order to assure congruency of data. Within PostgreSQL, [new tables](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/YouTube_Videos_ETL%20schema.sql) were created based off of the columns of the finalized DataFrames from the transformation step, with the video_id data set as the primary key. Once the tables were created,  an engine connection was initiated within Jupyter Notebook and all DataFrames were loaded into the database using the .to_sql function. 
* Canada_videos table
![](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/images/cavideossql.png)
* UK_videos table
![](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/images/gbvideossql.png)
* US_videos table
![](https://github.com/jwang711/SQL-projects/blob/master/SQL-ETL-Python_YouTube_Videos_Statistics/images/usvideossql.png)
