🏪 Project Overview – Retail Supply Chain Lakehouse Platform (RSCLP)
🧩 Business Context

The Retail Supply Chain Lakehouse Platform (RSCLP) models how data is managed for a single retail brand (example: “Daisy”) operating multiple stores.

In the current implementation, the platform represents one operational location with three suppliers, focusing on how daily retail activities are tracked, governed, and analyzed.

The objective of this project is to demonstrate how sales, deliveries, inventory movements, supplier orders, and profit calculations can be reliably managed using modern cloud data engineering practices.

🎯 What This Platform Solves

RSCLP answers key operational and analytical questions for a retail store, including:

What products were sold each hour?

When did inbound deliveries occur and from which suppliers?

How does inventory change after each sale or delivery?

How much was spent on supplier deliveries?

What is the daily profit at store and product level?

At the same time, the platform ensures:

✅ Data quality before processing

✅ Controlled and validated inventory updates

✅ Auditability of master data changes

✅ Analytics-ready datasets for reporting teams

🔄 End-to-End Data Flow
📥 Operational Data Generation

Sales transactions generated during store operations

Delivery and supplier order records from suppliers

Master data maintained through controlled Excel uploads

🧭 Orchestration

Azure Data Factory (ADF) orchestrates the entire workflow

Scheduled triggers for:

Sales

Deliveries

Profits

Supplier orders

Event-based triggers for master data uploads

File existence and schema validation before processing

⚙️ Data Processing

Azure Databricks is used for all transformations

Delta Live Tables (DLT) implement structured ETL/ELT pipelines

Data follows the Medallion Architecture:

Bronze: Raw ingested data

Silver: Validated and enriched data

Gold: Business-ready datasets

📦 Inventory Management

Inventory tables are updated only after pipeline validations pass

Sales reduce stock quantities

Deliveries increase stock quantities

Updates occur through controlled, automated workflows

🚨 Monitoring & Alerting

Azure Logic Apps sends automated alerts for:

Missing files

Schema validation failures

Pipeline or DLT job failures

📊 Analytics Consumption

Gold-layer Delta tables are exposed to analysts

Power BI dashboards provide insights into:

Sales performance

Inventory levels

Delivery spend

Daily profits

🏗️ Platform Design Principles

Single source of truth using Delta Lake

Governed data access via Unity Catalog

Fault-tolerant pipelines with automated alerting

Clear separation of concerns:

Orchestration → ADF

Processing → Databricks

Production-style CI/CD (Dev → Test → Prod)

📌 Scope Clarification

This project focuses on:

A single retail brand

One operational location

Structured operational data

End-to-end retail supply chain workflows

The design is scalable and can be extended to:

Multiple locations

Additional suppliers

More retail domains
