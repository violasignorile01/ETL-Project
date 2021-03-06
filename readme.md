# ETL - Extract, Transform, Load

"ETL is a type of data integration process referring to three distinct but interrelated steps (Extract, Transform and Load) and is used to synthesize data from multiple sources many times to build a Data Warehouse, Data Hub, or Data Lake." -Punit Pathak

## Extract

#### Original data sources and how the data was formatted (CSV, JSON, pgAdmin 4, etc)

* https://www.kaggle.com/stackoverflow/so-survey-2017¶
* https://www.kaggle.com/stackoverflow/stack-overflow-2018-developer-survey
* https://www.kaggle.com/mchirico/stack-overflow-developer-survey-results-2019

The above datasets were all converted to .csv format, in order to work with them in jupyternotebook

![csv.png](csv.png)

The above process was done with both 2018 and 2019 data sets as well.

## Transform:

#### The type of transformation needed for this data (cleaning, joining, filtering, aggregating, etc)

- Cleaned data - dropped NA's
- Inspected column names to find column names that contained the same info across all three years
- Filtered data - filtered only for columns that we wanted:
'id','gender','race','country','education_level','undergrad_major','years_coding','dev_type','salary'
- Renamed columns to be uniform across all 3 years (2017-2019)

## Load:

#### The type of final production database to load the data into (relational or non-relational)

- Relational database (.sql)

#### The final tables or collections that will be used in the production database

Below are the codes written to create each table, in Postgres, to then connect to our database:

![sql_tables.png](sql_tables.png)

- SQL Database: 'stackoverflow_survey_db'
- Tables within Database: 'survey_2017', 'survey_2018', 'survey_2019'

Below shows some of the code used to create and connect to the database:

![database.png](database.png)


The SQL database and tables were chosen so that survey would have a separate table with common elements across all 3 years.  

In the future, new tables can be added, with the same elements, iterating through the same process for each year (read in .CSV, clean, transform, insert into .SQL table, etc.)
