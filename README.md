# 🚲 Bike Sales Performance Data Pipeline

End-to-End Lakehouse Implementation in Databricks

# What Is This Project?

This project implements an end-to-end data engineering pipeline in Databricks that processes raw operational data from two independent source systems (CRM and ERP) and transforms it into analytics-ready dimensional models.

The goal is to simulate a real-world enterprise data platform where multiple operational systems feed a centralized Lakehouse architecture used for reporting and business intelligence.

This is not a single notebook workflow — it is a fully orchestrated, dependency-based pipeline built using Databricks Jobs.

# Project Objective

The objective of this project was to:
- Ingest raw transactional data from multiple systems
- Standardize and harmonize cross-system entities
- Apply business transformations
- Build a dimensional (star schema) model
- Orchestrate the entire process as a dependency-driven DAG
- Ensure deterministic and fault-isolated execution

In short:
Convert fragmented operational data into structured, analytics-ready data using a layered architecture.

# Data Pipeline Architecture (Databricks)
<img width="1475" height="650" alt="data_architecture2" src="https://github.com/user-attachments/assets/c5680838-938b-47c8-b533-da48f3869aa0" />

## Why This Architecture?
This design ensures scalability, fault isolation, and supports analytics and BI workloads using a modern Lakehouse approach.

# Overview

This project implements a multi-layer data pipeline (Bronze → Silver → Gold) in Databricks to process raw operational data and transform it into analytics-ready datasets.The pipeline is executed as a dependency-based Databricks Job, where each task runs only after its upstream dependencies have completed successfully.

Bronze Layer; Ingests raw data from ERP and CRM source systems No business logic applied Purpose: store raw, traceable, and auditable data Job: bronze

Silver Layer; Data cleansing and validation Normalization and application of business rules Domain-oriented transformations (Customer, Product, Location, Sales) Jobs: silver_erp_customer silver_erp_location silver_layer_customer silver_layer_crm_production silver_layer_erp_category silver_sales

Gold Layer; Builds analytics-ready tables using a star schema Optimized for BI tools and reporting Dimension Tables: gold_dim_customer gold_dim_product Fact Table: gold_fact_sales Fact Table: gold_fact_sales

Execution Flow The pipeline runs as a Directed Acyclic Graph (DAG) Task dependencies are managed by Databricks Jobs Downstream tasks execute only if upstream tasks succeed
  
## Technologies 
- Databricks 
- pyspark 
- Delta 
- Lake 
- GitHub

✅ Status Latest run: Successful All pipeline stages completed without errors
<img width="2941" height="1479" alt="pipeline_run3" src="https://github.com/user-attachments/assets/c13fee97-2075-49df-852a-926053f7f9ee" />

