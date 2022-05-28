# Project-2 Extract-Transform-Load Netflix Database
#### Team Members: Emmanuela, Nathaniel, Khadra
Group Project 2: Creating a Netflix Movies, TV Shows and Credits DataBase using SQL and Pandas
## Project Description
Our project is based on a three-phase process where our data is extracted from a source, transformed to illustrate the data in an organised way, and loaded into our chosen database. We have chosen two Netflix datasets, one pertains Netflix shows and movie titles, and the second one showcases the movie credits. 

## Extraction
We found our two Netflix datasets(titles.csv and credits.csv) on Kaggle and we imported the two csv files into dataframes using Pandas. 
## Transformation
The second step of the project consisted of cleaning datasets to showcase it in presentable way.
 On the credits dataframe we renamed the column ‘id’ to ‘movie_id’ as it was not clear what the column ‘id’ represented, and to facilitate merging the credit dataframe with the titles dataframe. The datasets were presented with some null values, however we decided not to drop all of those values because some columns had values showing as N/A (e.g., movies don’t have seasons). We also decided not to drop duplicates due to having multiple actors working in the same movie or tv shows. We decided to merge the two final dataframes to create a joint dataframe. We merged on movie_id, and ```how = left```. We noticed that the genre column and production country column in the merged dataframe had values that were arrays, thus to repaired them we used numpy. 

## Loading
The last step consisted of loading the dataframes into a database.
We created a database connection using create engine which we imported from sqlalchemy. We created the connection from Pandas to postgres sql (pgAdmin) onto our Neflix database which we created prior on pgAdmin.
We loaded our three dataframes onto Netflix database, using ```to.sql```, and saved our engine connection under the variable engine. 
We set the index as true, in order to use the index as primary key; the movie_id and the person_id columns had duplicated values; therefore, we could not use them as primary keys as they did not have unique values. 

## Final Step 
After we finished the loading step, we went to our Netflix Database that we created on pgAdmin and perfomed a quiery to comfirm that our database was successfully loaded. By performing these comands ``` SELECT * FROM titles ``` and ``` SELECT * FROM credits ```  and ``` SELECT * FROM titles_credits ```. 


## How to Run this Project

```python
import pandas as pd
from sqlalchemy import create_engine
from pg_keys import pg_key
import numpy as np
import ast
import random


* Install psycopg2 if not already installed
* Install sqlalchemy if not already installed
* Install numpy if not already installed
* Download PG Admin if not already downloaded
```
