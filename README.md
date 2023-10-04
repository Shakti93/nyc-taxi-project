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

![NYC Taxi ADF Pipeline](https://github.com/Shakti93/nyc-taxi-project/assets/84408451/44b2257d-8a53-4e4e-893c-552b49c52338)

1. **Data Sources:** The data sources for this pipeline are NYC.org and GitHub. The data sources contain files for trip data which are in parquet format distributed month-wise from the year 2012 till the latest month. Dimension data is stored in CSV format in GitHub for Payment Mode, Rate, Borough and Zone, Vendor, and Calendar. 
2. **Data Ingestion:** The data is extracted from NYC.org and Github Repository using HTTP Protocol Linked Service in Azure Data Factory to Azure Data Lake Storage and stored in the NYC raw container. ADF pipelines are created to fetch monthly data on 1st day of each month using the Tumbling Window Trigger. 
3. **Data Transformation:** The raw data is transformed using Azure Databricks. The transformation process includes data cleaning, data validation, and data enrichment. Exploratory data analysis (EDA) is performed to understand data patterns and anomalies. The transformed data is stored in the NYC processed container as Tables. Trip data is incrementally loaded into delta tables to ensure that only data for the current month is loaded and updated data to reduce the processing cost and time. Delta tables also provide transactional capabilities, versioning, and schema enforcement. 
5. **Data Warehousing:** Processed trip data along with DIM tables is stored in SQL Server which will be used for Data Warehousing and for future analysis and Visualization in Power BI 
5. **Data Visualization:** Power BI is used for visualizing and creating interactive dashboards. The dashboard includes charts, graphs, and maps to showcase trends, ride patterns, fare distributions, and more. 

## Power BI Dashboard 

![NYC PowerBI Report](https://github.com/Shakti93/nyc-taxi-project/assets/84408451/5418bfb7-1043-4844-aab5-fc366f370667)

The visualizations for the Power BI dashboard include- 

1. Key Performance Indicator (KPI) cards that provide insights into Total Rides, Average Fare, Average Trip Distance, and Average Trip Duration within a specific filter context.
2. A dynamic Line Chart with parameterization, enabling the display of trends in Total Rides, Average Fare, Average Trip Distance, and Average Trip Duration over the course of the past year.
3. A Bar Graph illustrating the hourly distribution of Total Rides, Average Fare, Average Trip Distance, and Average Trip Duration, facilitating a comprehensive view of time-based patterns.
4. A Horizontal Bar Graph depicting the distribution of rides by Borough, allowing for easy comparison and analysis of ride distribution across different geographic areas.
5. A Map visualization presenting the spatial density of rides by location, allowing for a visual exploration of ride hotspots.
6. A Donut Chart representing the distribution of payment modes, providing an overview of how customers choose to pay for their rides.


## Project highlights  

1. Proficiently orchestrated a comprehensive data pipeline within Azure services, encompassing data ingestion, storage, cleaning, transformation, and analysis of New York taxi data, ensuring seamless data flow and management.
2. Crafted an intuitive Power BI dashboard that empowers users to conduct in-depth comparisons of ride fares, trip lengths, timings, and boroughs, with the flexibility to explore and analyze multiple influencing factors.


## Conclusion 

This project showcases the effective utilization of Azure services to handle and analyze large and complex datasets. The insights gained from comparing taxi ride attributes can be invaluable for taxi service providers and city planners 
