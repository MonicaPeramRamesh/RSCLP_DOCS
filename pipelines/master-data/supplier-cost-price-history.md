# Supplier Cost Price History Pipeline (SCD Type 2)

## Overview
Tracks historical supplier cost prices for products to support inventory valuation and profit analysis.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on supplier cost updates, including pre-run schema validation.

## Processing
Built using Azure Databricks and Delta Live Tables, following the Medallion Architecture.

## Change Data Handling
Supplier cost changes are managed using SCD Type 2 with DLT `APPLY CHANGES` to ensure historical accuracy.

## Reliability & Governance
Data quality checks, schema enforcement, and Logic Apps–based alerting for failures or data issues.

## Dependencies
Used by inbound deliveries, inventory updates, and daily profit computation pipelines.

## Snapshots
- ADF orchestration pipeline  
- Databricks DLT DAG  
- Logic Apps alert workflow  

## Code
Implementation is available in the Databricks repository:  
➡️ https://github.com/<your-org>/RSCLP_ADB
