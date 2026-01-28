# Daily Sales Pipeline

## Overview
Processes sales transactions from the retail store every hour and generates standardized sales facts for inventory and profit calculations.

## Orchestration
Azure Data Factory pipeline triggered **hourly** on sales file arrival, with schema validation and control checks before execution.

## Processing
Implemented using Azure Databricks and Delta Live Tables, following the **Medallion Architecture (Bronze → Silver → Gold)** to transform raw sales data into analytics-ready facts.

## Core Logic
- Validate product references against Product Master  
- Aggregate hourly and daily sales metrics  
- Apply discounts, promotions, and pricing logic  
- Generate sales-level facts for inventory and profit calculations  

## Reliability & Governance
- Schema enforcement and referential integrity checks  
- External Delta tables in ADLS for secure, auditable storage  
- Azure Logic Apps alert workflow for pipeline or data failures  

## Dependencies
- Product Master  
- Product Price History  

## Snapshots
- Azure Data Factory orchestration pipeline (hourly trigger)  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  
- Automated Test Case Execution (Pytest) – snapshot of test coverage and validation results  

## Code & Automated Tests
The full implementation and validation framework for this pipeline is maintained in two separate repositories:

- **Databricks Implementation (DLT pipelines)**  
  ➡️ https://github.com/<your-org>/RSCLP_ADB  

- **Automated Tests & Validation (Pytest framework)**  
  ➡️ https://github.com/<your-org>/RSCLP_TEST
