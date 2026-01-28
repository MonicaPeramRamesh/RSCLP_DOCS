# Supplier Orders Pipeline

## Overview
Processes supplier order data and generates standardized order facts for inventory planning and cost analysis.

## Orchestration
Azure Data Factory pipeline triggered on supplier order file arrival, with schema validation and control checks before execution.

## Processing
Implemented using Azure Databricks and Delta Live Tables, following the **Medallion Architecture (Bronze → Silver → Gold)** to transform raw orders into analytics-ready datasets.

> **Note:** Supplier order data originates as JSON files and is converted into Parquet format for optimized processing.

## Core Logic
- Validate product and supplier references against master data  
- Apply cost prices from Supplier Cost Price History  
- Generate standardized supplier order facts for downstream pipelines  

## Reliability & Governance
- Schema enforcement and referential integrity checks  
- External Delta tables in ADLS for secure, auditable storage  
- Azure Logic Apps alert workflow for pipeline or data failures  

## Dependencies
- Product Master  
- Supplier Cost Price History  

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  

## Code
Databricks implementation is maintained in the repository:  
➡️ https://github.com/<your-org>/RSCLP_ADB
