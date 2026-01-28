# Inbound Deliveries Pipeline

## Overview
Processes inbound product deliveries from suppliers and records delivery facts with accurate cost attribution for inventory and profit calculations.

## Orchestration
Azure Data Factory pipeline triggered on inbound delivery file arrival, with schema validation and control checks before execution.

## Processing
Implemented using Azure Databricks and Delta Live Tables, applying the **Medallion Architecture (Bronze → Silver → Gold)**.

Delta Live Tables write **Delta files to ADLS**, which are exposed as **Unity Catalog external tables** for governed access.

## Core Logic
- Validate product and supplier references against master data  
- Apply effective supplier cost price based on delivery date  
- Generate standardized inbound delivery fact tables  

## Reliability & Governance
- Schema enforcement and referential integrity checks  
- Unity Catalog external tables for centralized access control and auditability  
- Azure Logic Apps for alerting on validation failures or pipeline errors  

## Dependencies
- Product Master  
- Supplier Cost Price History  

## Snapshots
- Azure Data Factory orchestration pipeline  
- Databricks Delta Live Tables (DLT) DAG  
- Azure Logic Apps alert workflow  

## Code
Databricks implementation is available at:  
➡️ https://github.com/<your-org>/RSCLP_ADB
