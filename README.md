# NY-Energy-Data-Pipeline-Automation

## Data Scope
* Hourly demand for electricity by subregion
* All subregions under NYIS or New York Independent System Operator
* Refresh daily

## Data Pipeline Requirements
* Fully automate
* High level of customization
* Data quality checks and unit tests
* Monitor

## Data pipeline architecture
* EIA API - is the source data/raw data
* Data Automation - checks if new data is available and refresh the data when applicable and collects metadata on each steps enabling us to monitor the health of the data pipeline
* Local Environment - has the backfill function to restart the pipeline whenever needed and backfill all this local data
* Typically it is better to separate refresh and backfill process and the initial data pull of this local data might be heavy and require more compute resources than available on the scheduler (ie; Github Actions here)
* Data Visualization - a dashboard on Github Pages that will enable us to view the data and track the logs
* Once the data pipeline finishes updating the data with new data points, GitHub actions will update the dashboard with new data

## ETL Supporting Functions
* Data processing - full data from the API, transforming it from JSON objects into DataFrame object, creating and updating the metadata and append new data into the normalized table
* create_metadata - the function creates the metadata table for giving data input. It then ran some unit tests to evaluate if the data refresh was successful, and if we can append the new data to the normalized table
* load_metadata - is an helper function that reads the series details and merge it with the metadata logs
* get_metadata - this function checks if there are any new incremental data points or difference between the data in the source and normalized table by comparsing the normalized log and the corresponding metadata available in the API
* append_metadata - appends new metadata that is created during the refresh process with the metadata table
* append_data - append new data points to the normalized table
* eia_metadata and eia_backfill


