# Daily Profit Computation Pipeline

## Overview
Calculates daily profits at store and product level by combining sales, inventory, and supplier cost data.

## Orchestration
Triggered by **Azure Data Factory** after all relevant upstream pipelines (Daily Sales, Inbound Deliveries, Supplier Orders) have completed successfully.  

## Processing
Implemented using **Azure Databricks** to compute business-ready profit facts directly from validated input data.

## Core Logic
- Merge sales revenue with cost of goods sold (COGS)  
- Apply supplier cost prices from inbound deliveries  
- Compute gross profit and daily profit metrics  

## Reliability & Governance
- Schema enforcement and referential integrity checks  
- Logic Apps alerts for missing data or pipeline failures  
- Output stored as **external Delta tables in ADLS**  

## Dependencies
- Daily Sales Pipeline  
- Inbound Deliveries Pipeline  
- Supplier Orders Pipeline  
- Product Master & Supplier Cost Price History  

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks pipeline DAG (execution flow)  
- Azure Logic Apps alert workflow  

## Code
- Databricks implementation:  
➡️ https://github.com/<your-org>/RSCLP_ADB
