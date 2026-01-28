# Product Price History Pipeline (SCD Type 2)

## Overview
Tracks historical selling price changes for products to support accurate revenue and profit analysis.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on price update file arrival, including schema validation checks.

## Processing
Built using Azure Databricks and Delta Live Tables, applying the **Medallion Architecture** for structured transformations.

Delta tables are stored in **ADLS** and registered as **Unity Catalog external tables**.

## Change Data Handling
Selling price changes are handled using **SCD Type 2**, enabling time-based price analysis through DLT `APPLY CHANGES`.

## Reliability & Governance
- Schema enforcement and business rule validation  
- Unity Catalog external tables for secure, governed access  
- Azure Logic Apps for pipeline and data-quality alerts  

## Dependencies
Consumed by:
- Daily Sales  
- Daily Profit Computation  

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  

## Code
Databricks implementation is available at:  
➡️ https://github.com/<your-org>/RSCLP_ADB
