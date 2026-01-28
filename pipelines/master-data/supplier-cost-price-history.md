# Supplier Cost Price History Pipeline (SCD Type 2)

## Overview
Tracks historical supplier cost prices for products to support inventory valuation and profit computation.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on supplier cost update file arrival, with pre-run schema validation.

## Processing
Implemented using Azure Databricks and Delta Live Tables, following the **Medallion Architecture (Bronze → Silver → Gold)**.

Processed Delta tables are stored in **ADLS** and exposed via **Unity Catalog external tables**.

## Change Data Handling
Supplier cost changes are managed using **SCD Type 2** with DLT `APPLY CHANGES` to ensure historical accuracy.

## Reliability & Governance
- Schema enforcement and data quality checks  
- Unity Catalog external tables for centralized governance  
- Azure Logic Apps–based alerting for failures and validation issues  

## Dependencies
Consumed by:
- Inbound Deliveries  
- Inventory Management  
- Daily Profit Computation  

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  

## Code
Databricks implementation is available at:  
➡️ https://github.com/<your-org>/RSCLP_ADB
