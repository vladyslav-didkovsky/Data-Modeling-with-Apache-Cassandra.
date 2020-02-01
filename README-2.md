#Introduction: <h1> tag 

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. There is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app. My role is to create an Apache Cassandra database which can create queries on song play data to answer the questions.

#Project Overview: <h1> tag 

In this project, I would be applying Data Modeling with Apache Cassandra and complete an ETL pipeline using Python. I am provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables.

#Datasets: <h1> tag 

For this project, you'll be working with one dataset: event_data. The directory of CSV files partitioned by date. Here are examples of filepaths to two files in the dataset: event_data/2018-11-08-events.csv event_data/2018-11-09-events.csv

#Project Template:<h1> tag 

The project template includes one Jupyter Notebook file, in which: 
1.You will process the event_datafile_new.csv dataset to create a denormalized dataset 
1.You will model the data tables keeping in mind the queries you need to run 
1.You have been provided queries that you will need to model your data tables for you
1.You will load the data into tables you create in Apache Cassandra and run your queries

###Project Steps:<h3> tag 


#Modelling your NoSQL Database or Apache Cassandra Database:<h1> tag 

1.Design tables to answer the queries outlined in the project template
1.Write Apache Cassandra CREATE KEYSPACE and SET KEYSPACE statements
1.Develop your CREATE statement for each of the tables to address each question
1.Load the data with INSERT statement for each of the tables
1.Include IF NOT EXISTS clauses in your CREATE statements to create tables only if the tables do not already exist. We recommend you also include DROP TABLE statement for each table, this way you can run drop and create tables whenever you want to reset your database and test your ETL pipeline
1.Test by running the proper select statements with the correct WHERE clause

#CHEATS - Build ETL Pipeline: <h1> tag

1.Implement the logic in section Part I of the notebook template to iterate through each event file in event_data to process and create a new CSV file in Python
1.Make necessary edits to Part II of the notebook template to include Apache Cassandra CREATE and INSERT three statements to load processed records into relevant tables in your data model
1.Test by running three SELECT statements after running the queries on your database
1.Finally, drop the tables and shutdown the cluster

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

Dataset

There is one dataset called event_data which is in a directory of CSV files partitioned by date. The filepaths are given as event_data/<yyyy>-<mm>-<dd>-events.csv where <yyyy> indicates the year, <mm> indicates the month and <dd> indicates the year. The fields of of event_data are:

1.artist (string)
1.auth (string)
1.firstName (string)
1.gender (char)
1.itemInSession (int)
1.lastName (string)
1.length (float)
1.level (string)
1.location (string)
1.method (string)
1.page (string)
1.registration (float)
1.sessionId (int)
1.song (string)
1.status (int)
1.ts (float)
1.userId (int)


###Queries - FAST-PLAN-WHAT_SHOULD_I_DO? <h3> tag
    
#For NoSQL databases, we design the schema based on the queries we know we want to perform. For this project, we have three queries:<h1> tag

1.Find artist, song title and song length that was heard during sessionId=338, and itemInSession=4.SELECT artist, song, length from table_1 WHERE sessionId=338 AND itemInSession=4
1.Find name of artist, song (sorted by itemInSession) and user (first and last name) for userid=10, sessionId=182.SELECT artist, song, firstName, lastName FROM table_2 WHERE userId=10 and sessionId=182
1.Find every user name (first and last) who listened to the song 'All Hands Against His Own'.SELECT firstName, lastName WHERE song='All Hands Againgst His Own'

##Schema <h2> tag

#For the first query: <h1> tag

1.Column 1 = sessionId
1.Column 2 = itemInSession
1.Column 3 = artist
1.Column 4 = song
1.Column 5 = length
1.Primary key = (sessionId, itemInSession)

#For the second query:<h1> tag 

1.Column 1 = userId
1.Column 2 = sessionId
1.Column 3 = artist
1.Column 4 = song
1.Column 5 = itemInSession
1.Column 6 = firstName
1.Column 7 = lastName
1.Primary key = (userId, sessionId) with clustering column itemInSession

#For the third query:<h1> tag

1.Column 1 = song
1.Column 2 = firstName
1.Column 3 = lastName
1.Primary key = (song)

##ETL Pipeline <h2> tag

1.Start with the raw csv data files as described in Dataset
1.For each row of the csv data, insert the data in the appropriate column as described in Schema
1.Perform the Select query as described in Queries
1.Build Instructions

###Run each portion of Project_1B_Project_Template.ipynb. WOW, LOOK AT THAT:D U have done this project. <h3> tag