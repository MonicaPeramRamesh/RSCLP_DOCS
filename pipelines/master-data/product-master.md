# Product Master Pipeline (SCD Type 2)

## Overview
Maintains the authoritative product master dataset used across all retail processes, including sales, inventory, deliveries, and analytics.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on product master file arrival, with schema and mandatory field validation before execution.

## Processing
Implemented using Azure Databricks and Delta Live Tables, following the **Medallion Architecture (Bronze → Silver → Gold)**.

Delta outputs are stored in **ADLS** and exposed as **Unity Catalog external tables** for governed access.

## Change Data Handling
Product attribute changes are managed using **SCD Type 2** with DLT `APPLY CHANGES`, preserving full historical lineage.

## Reliability & Governance
- Schema enforcement and data quality rules  
- Unity Catalog external tables for centralized governance and auditability  
- Azure Logic Apps for alerting on validation or pipeline failures  

## Dependencies
Referenced by all downstream operational and analytical pipelines.

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  

## Code
Databricks implementation is available at:  
➡️ https://github.com/<your-org>/RSCLP_ADB
