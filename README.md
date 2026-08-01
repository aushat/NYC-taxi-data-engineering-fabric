# 🚕 NYC Taxi Data Engineering Project using Microsoft Fabric

## 📖 Overview

This project demonstrates the design and implementation of an end-to-end data engineering solution using Microsoft Fabric. Monthly New York City Yellow Taxi trip data is ingested from Parquet files into a Fabric Lakehouse, processed through automated Data Factory pipelines, transformed using SQL stored procedures and Dataflow Gen2, loaded into a Fabric Data Warehouse, and visualized through an interactive Power BI dashboard.

The solution supports incremental monthly data processing, allowing newly available datasets to be appended to the presentation layer without reprocessing historical records. This project showcases core data engineering concepts including ETL orchestration, data transformation, automation, warehousing, semantic modeling, and business intelligence reporting.

## 🏗️ Solution Architecture

The diagram below illustrates the end-to-end data flow implemented in Microsoft Fabric.

![Solution Architecture](images/architecture.png)

## ⚙️ Technology Stack

| Technology | Purpose |
|------------|---------|
| **Microsoft Fabric** | End-to-end data engineering platform |
| **Fabric Lakehouse** | Stores raw NYC Yellow Taxi Parquet files |
| **Data Factory Pipelines** | Automates data ingestion and orchestration |
| **SQL** | Data validation, filtering, and stored procedures |
| **Dataflow Gen2** | Data cleansing, transformation, and enrichment |
| **Fabric Data Warehouse** | Stores staging and presentation tables |
| **Semantic Model** | Provides a reporting layer for Power BI |
| **Power BI** | Interactive dashboard and business intelligence reporting |
| **Parquet Files** | Raw data storage format |


## 📊 Dataset

This project uses the **New York City Yellow Taxi Trip Records** dataset published by the NYC Taxi & Limousine Commission (TLC) - https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page. The dataset contains monthly trip-level information including pickup and dropoff timestamps, passenger counts, trip distances, fares, payment methods, and pickup/dropoff locations. It has the following data dictionary as well : https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf.

Each monthly dataset is stored in **Parquet** format and ingested into Microsoft Fabric for automated processing.


## 🔄 Project Workflow

The project follows an end-to-end ETL workflow that automates the ingestion, transformation, and reporting of NYC Taxi trip data.

### 1️⃣ Data Ingestion

Monthly NYC Yellow Taxi datasets are downloaded in Parquet format and uploaded to a Fabric Lakehouse, which serves as the raw data storage layer. A separate Taxi Zone Lookup dataset is also uploaded to enrich trip records with readable pickup and dropoff locations.

> 📷 **Lakehouse**
>
> ![Lakehouse](images/lakehouse.png)
>
> 
### 2️⃣ Data Warehouse

A Fabric Data Warehouse was created to manage the analytical data model. Staging tables temporarily store newly ingested records, while presentation tables contain cleaned and transformed data ready for reporting.

> 📷 **Warehouse**
>
> ![Warehouse](images/warehouse.png)

### 3️⃣ Data Pipelines

Multiple Data Factory pipelines were developed to automate the ETL workflow.

- **pl_stg_lookup** loads the Taxi Zone Lookup table into the staging layer.
- **pl_stg_processing_nyctaxi** copies raw taxi data into staging tables and executes SQL stored procedures.
- **pl_pres_processing_nyctaxi** transforms and loads cleaned data into presentation tables.
- **pl_orchestrate_nyctaxi** orchestrates the entire workflow by executing all pipelines in sequence, enabling automated monthly processing.

> 📷 **Data Pipelines**
>
> ![Pipelines](images/pipelines.png)
