# Supplier Cost Price History Pipeline (SCD Type 2)

## Overview
Tracks historical supplier cost prices for products to support inventory valuation and profit analysis.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on supplier cost updates, including pre-run schema validation.

## Processing
Built using Azure Databricks and Delta Live Tables, following the **Medallion Architecture (Bronze → Silver → Gold)** with Delta tables stored in ADLS.

## Change Data Handling
Supplier cost changes are managed using SCD Type 2 with DLT `APPLY CHANGES` to ensure historical accuracy.

## Reliability & Governance
Schema enforcement, data quality rules, and controlled writes to ADLS-backed Delta tables.
Azure Logic Apps provide alerting for validation failures or pipeline errors.

## Dependencies
Used by inbound deliveries, inventory updates, and daily profit computation pipelines.

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  

## Code
Databricks implementation is available at:  
➡️ https://github.com/<your-org>/RSCLP_ADB
