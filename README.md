# 🚕 NYC Taxi Data Engineering Project using Microsoft Fabric

## 📖 Overview

This project demonstrates the design and implementation of an end-to-end data engineering solution using Microsoft Fabric. Monthly New York City Yellow Taxi trip data is ingested from Parquet files into a Fabric Lakehouse, processed through automated Data Factory pipelines, transformed using SQL stored procedures and Dataflow Gen2, loaded into a Fabric Data Warehouse, and visualized through an interactive Power BI dashboard.

The solution supports incremental monthly data processing, allowing newly available datasets to be appended to the presentation layer without reprocessing historical records. This project showcases core data engineering concepts including ETL orchestration, data transformation, automation, warehousing, semantic modeling, and business intelligence reporting.

## 🏗️ Solution Architecture

The diagram below illustrates the end-to-end data flow implemented in Microsoft Fabric.

![Solution Architecture](images/architecture.png)
