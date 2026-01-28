
# Product Price History Pipeline (SCD Type 2)

## Overview
Maintains historical selling prices for products to support accurate sales valuation and profit calculations.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on price update file uploads, with schema validation prior to execution.

## Processing
Implemented in Azure Databricks using Delta Live Tables with a Bronze → Silver → Gold architecture.

## Change Data Handling
Price changes are captured using SCD Type 2 via DLT `APPLY CHANGES`, preserving full price history.

## Reliability & Governance
Schema enforcement, price sanity checks, and automated alerting via Logic Apps for validation or execution failures.

## Dependencies
Consumed by daily sales and daily profit computation pipelines.

## Snapshots
- ADF orchestration pipeline  
- Databricks DLT DAG  
- Logic Apps alert workflow  

## Code
Implementation is available in the Databricks repository:  
➡️ https://github.com/<your-org>/RSCLP_ADB
