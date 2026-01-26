# Project Overview – Retail Supply Chain Lakehouse Platform (RSCLP)

## Business Context

The **Retail Supply Chain Lakehouse Platform (RSCLP)** models how data is managed for a **single retail brand** (example: *Daisy*) operating multiple stores.

In the current implementation, the platform represents **one operational location with three suppliers**, focusing on how daily retail operations are tracked, governed, and analyzed.

The objective of this project is to demonstrate how **store activities such as sales, deliveries, inventory movements, supplier orders, and profit computation** can be reliably managed using modern cloud data engineering practices.

---

## What This Platform Solves

RSCLP answers key **operational and analytical questions**, such as:

- What products were sold each hour?
- When did inbound deliveries occur and from which suppliers?
- How does inventory change after each sale or delivery?
- How much was spent on supplier deliveries?
- What is the daily profit at store and product level?

At the same time, the platform ensures:

- **Data quality validation before processing**
- **Controlled inventory updates**
- **Auditability of master data changes**
- **Analytics-ready datasets**

---

## End-to-End Data Flow

### Operational Data Generation

- Sales transactions generated during store operations  
- Delivery and supplier order records from suppliers  
- Master data maintained through controlled Excel uploads  

---

### Orchestration

- **Azure Data Factory (ADF)** orchestrates the entire workflow
- **Scheduled triggers** for:
  - Sales
  - Deliveries
  - Supplier orders
  - Daily profit computation
- **Event-based triggers** for master data uploads
- File existence and schema validation before execution

---

### Data Processing

- **Azure Databricks** handles all transformations
- **Delta Live Tables (DLT)** implement structured ETL / ELT pipelines
- **Medallion Architecture**:
  - **Bronze** – Raw ingested data
  - **Silver** – Cleansed and validated data
  - **Gold** – Business-ready datasets

---

### Inventory Management

- Inventory updates occur **only after pipeline validations pass**
- Sales transactions **reduce stock**
- Inbound deliveries **increase stock**
- Updates are fully automated and governed

---

### Monitoring and Alerting

- **Azure Logic Apps** sends alerts for:
  - Missing input files
  - Schema validation failures
  - Pipeline execution failures
  - DLT job failures

---

### Analytics Consumption

- **Gold-layer Delta tables** exposed to analytics users
- **Power BI dashboards** provide insights into:
  - Sales performance
  - Inventory thresholds
  - Delivery spend
  - Daily profit trends

---

## Platform Design Principles

- **Single source of truth** using Delta Lake
- **Governed access** via Unity Catalog
- **Fault-tolerant pipelines** with alerts
- **Separation of concerns**:
  - Orchestration → ADF
  - Processing → Databricks
- **Production-grade CI/CD** (Dev → Test → Prod)

---

## Scope Clarification

This project focuses on:

- One retail brand
- One operational location
- Structured operational data
- End-to-end supply chain workflows

The design is **scalable** and can be extended to:

- Multiple locations
- Additional suppliers
- More retail domains

---

## Purpose of This Documentation

This repository documents:

- Architecture decisions
- Pipeline designs
- Orchestration patterns
- Data governance and testing strategy

**Target audience:**

- Hiring managers
- Data engineering interviewers
- Solution architects
