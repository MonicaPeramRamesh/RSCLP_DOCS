# Inbound Deliveries Pipeline

## Overview
Processes inbound product deliveries from suppliers and records delivery facts with correct cost attribution for inventory and profit calculations.

## Orchestration
Azure Data Factory pipeline triggered on inbound delivery file arrival, with schema validation and control checks before execution.

## Processing
Implemented using Azure Databricks and Delta Live Tables, leveraging the **Medallion Architecture (Bronze → Silver → Gold)** to transform raw deliveries into analytics-ready facts.

## Core Logic
- Validate product and supplier references against master data  
- Apply effective supplier cost price based on delivery date  
- Generate standardized inbound delivery facts  

## Reliability & Governance
- Schema enforcement and referential integrity checks  
- Unity Catalog external tables in ADLS for secure, auditable data access  
- Azure Logic Apps alert workflow for pipeline or data failures  

## Dependencies
- Product Master  
- Supplier Cost Price History  

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  
- Automated Test Case Execution (Pytest) – snapshot of test coverage and validation results  

## Code & Automated Tests
The full implementation and validation framework for this pipeline is maintained in two separate repositories:

- **Databricks Implementation (DLT pipelines)**  
  ➡️ https://github.com/<your-org>/RSCLP_ADB  

- **Automated Tests & Validation (Pytest framework)**  
  ➡️ https://github.com/<your-org>/RSCLP_TEST
