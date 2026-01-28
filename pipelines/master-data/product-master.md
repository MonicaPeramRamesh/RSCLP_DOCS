# Product Master Pipeline (SCD Type 2)

## Overview
Manages product master data with full historical tracking to support sales, inventory, deliveries, and profit analytics.

## Orchestration
Event-driven Azure Data Factory pipeline triggered on master data uploads, with pre-execution schema validation.

## Processing
Implemented in Azure Databricks using Delta Live Tables, following a Bronze → Silver → Gold pattern.

## Change Data Handling
Product attribute changes are tracked using SCD Type 2 via DLT `APPLY CHANGES`, ensuring auditability.

## Reliability & Governance
Schema enforcement, data quality checks, and automated alerting via Logic Apps for validation or pipeline failures.

## Dependencies
Downstream consumers include sales, inventory, inbound deliveries, and profit computation pipelines.

## Snapshots
- ADF orchestration pipeline  
- Databricks DLT DAG  
- Logic Apps alert workflow  

## Code
Implementation is available in the Databricks repository:  
➡️ https://github.com/<your-org>/RSCLP_ADB
