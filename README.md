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
