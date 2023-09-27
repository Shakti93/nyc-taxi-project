# Analyzing NYC Taxi Data in Azure Environment


## Introduction 

The New York City Taxi and Limousine Commission (TLC) provides extensive data on taxi trips in the city, including information on fares, trip durations, timings, and boroughs. This project utilizes Azure cloud services to ingest, store, clean, transform, and analyze New York taxi data for the last 10 years. Additionally, the project aims to create a Power BI dashboard for comparing various aspects of taxi rides and their dependency on factors like seasons, months, weekdays/weekends, and time of day. 

### Project Objectives 

1. **Data Ingestion:** Ingest monthly data from NYC.org in Parquet format starting from 2012 till the latest month using Azure Data Factory (ADF). 
2. **Data Storage:** Store the ingested data in the NYC Raw container in Azure Data Lake Storage (ADLS). 
3. **Data Cleaning and Transformation:** Perform data cleaning and transformation using Azure Databricks and storing them as Delta tables in processed containers. 
4. **Data Modelling:** Add new Dimension tables for Payment Mode, Rate, Borough and Zone, Vendor, and Calendar. 
5. **Data Processing and Warehousing:** Process and aggregate data, and in an Azure SQL Database. 
6. **Data Visualization:** Create a Power BI dashboard for visualizing and comparing various aspects of taxi rides. 

## Solution Architecture

![NYC solution diagram](https://github.com/Shakti93/nyc-taxi-project/assets/84408451/528b297c-fe6e-401c-b660-e8b017d2abf3)

## Data Pipeline Implementation 

1. **Data Sources:** The data sources for this pipeline are NYC.org and GitHub. The data sources contain files for trip data which are in parquet format distributed month-wise from the year 2012 till the latest month. Dimension data is stored in CSV format in GitHub for Payment Mode, Rate, Borough and Zone, Vendor, and Calendar. 
2. **Data Ingestion:** The data is extracted from NYC.org and Github Repository using HTTP Protocol Linked Service in Azure Data Factory to Azure Data Lake Storage and stored in the NYC raw container. ADF pipelines are created to fetch monthly data on 1st day of each month using the Tumbling Window Trigger. 
3. **Data Transformation:** The raw data is transformed using Azure Databricks. The transformation process includes data cleaning, data validation, and data enrichment. Exploratory data analysis (EDA) is performed to understand data patterns and anomalies. The transformed data is stored in the NYC processed container as Tables. Trip data is incrementally loaded into delta tables to ensure that only data for the current month is loaded and updated data to reduce the processing cost and time. Delta tables also provide transactional capabilities, versioning, and schema enforcement. 
5. **Data Warehousing:** Processed trip data along with DIM tables is stored in SQL Server which will be used for Data Warehousing and for future analysis and Visualization in Power BI 
5. **Data Visualization:** Power BI is used for visualizing and creating interactive dashboards. The dashboard includes charts, graphs, and maps to showcase trends, ride patterns, fare distributions, and more. 

## Power BI Dashboard 

1. The visualizations for the Power BI dashboard include-  
2. KPI cards for Total Rides, Average Fare, Average Trip Distance, and Average Trip Duration for a particular Filter context. 
3. Parameterized Line Chart to show Total Rides, Average Fare, Average Trip Distance, and Average Trip Duration over the past 1 year. 
4. Bar Graph for hourly distribution of Total Rides, Average Fare, Average Trip Distance, and Average Trip Duration. 
5. Horizontal Bar Graph for distribution of rides by Borough 
6. Map visualization for density of rides by location. 


## Project highlights  

1. Successfully implemented a data pipeline for ingesting, storing, cleaning, transforming, and analyzing New York taxi data using Azure services. 
2. Created a Power BI dashboard for comparing ride fares, lengths, timings, and boroughs based on various factors. 


## Conclusion 

This project showcases the effective utilization of Azure services to handle and analyze large and complex datasets. The insights gained from comparing taxi ride attributes can be invaluable for taxi service providers and city planners 
