# Retail Supply Chain Lakehouse Platform (RSCLP)

> **End-to-end enterprise Retail Supply Chain Lakehouse built using Azure Databricks, Delta Live Tables, Azure Data Factory, Unity Catalog, and Azure DevOps CI/CD**

This repository serves as the **official technical documentation and proof-of-work** for the RSCLP project. Code repositories for Databricks pipelines and automated tests are maintained separately.

---

## 🔗 Related Repositories

| Repository                 | Purpose                                                  |
| -------------------------- | -------------------------------------------------------- |
| **RSCLP_ADB**              | Databricks DLT pipelines, notebooks, jobs                |
| **RSCLP_TEST**             | PyTest-based data quality and pipeline validation tests  |
| **RSCLP_DOCS (this repo)** | Architecture, pipeline design, orchestration, dashboards |

---

## 📌 Project Overview

The **Retail Supply Chain Lakehouse Platform (RSCLP)** is designed to support core retail operations and analytics by processing data across multiple business domains:

* Daily Sales (hourly ingestion)
* Inbound Deliveries (multi-daily ingestion)
* Inventory Management (sales & deliveries driven)
* Supplier Orders
* Daily Profit Computation
* Master Data Management (SCD Type 2)

The platform follows **Lakehouse + Medallion Architecture** principles and is built with **production-grade governance, validation, monitoring, and CI/CD**.

---

## 🏗️ High-Level Architecture

**Orchestration**

* Azure Data Factory (ADF)

  * Scheduled triggers (hourly / daily)
  * Event-based triggers (Excel-based master data uploads)
  * File existence & schema validation

**Processing & Storage**

* Azure Databricks
* Delta Live Tables (DLT)
* Delta Lake (Open Table Format)
* Unity Catalog (Catalog → Schema → Tables)

**Monitoring & Alerts**

* Azure Logic Apps
* Automated email alerts for:

  * Missing files
  * Schema validation failures
  * DLT job failures

**Analytics & Consumption**

* Gold-layer Delta tables
* Power BI dashboards

---

## 🥇 Medallion Architecture

| Layer  | Description                         |
| ------ | ----------------------------------- |
| Bronze | Raw ingested data (as-is)           |
| Silver | Cleansed, validated, enriched data  |
| Gold   | Business-ready, aggregated datasets |

Each business domain is implemented as an **independent Delta Live Tables pipeline** following this pattern.

---

## 🧩 Business Domains

| Domain             | Pipeline Type | Frequency                 |
| ------------------ | ------------- | ------------------------- |
| Master Data        | Event-based   | On file upload            |
| Daily Sales        | Scheduled     | Hourly (7 AM – 11 PM)     |
| Inbound Deliveries | Scheduled     | 3 times/day               |
| Inventory          | Derived       | Sales & Deliveries driven |
| Supplier Orders    | Scheduled     | Daily                     |
| Daily Profits      | Scheduled     | End of day                |

---

## 📂 Detailed Pipeline Documentation

Each pipeline is documented with **architecture, orchestration, DLT logic, data quality, and failure handling**.

➡️ **Start Here:**

* [Master Data Management](./pipelines/master-data.md)
* [Inbound Deliveries](./pipelines/inbound-deliveries.md)
* [Daily Sales](./pipelines/daily-sales.md)
* [Inventory Management](./pipelines/inventory.md)
* [Supplier Orders](./pipelines/supplier-orders.md)
* [Daily Profit Computation](./pipelines/daily-profits.md)

---

## 🔁 CI/CD & Testing Strategy

* Git-based source control (Azure DevOps)
* Separate repositories for pipelines and tests
* Automated deployment across **Dev → Test → Prod**
* PyTest-based validations executed before deployment
* Manual approval gates for higher environments

➡️ Detailed CI/CD flow documented here:

* [CI/CD & Testing](./cicd/cicd-overview.md)

---

## 📊 Analytics & Dashboards

Power BI dashboards built on Gold-layer Delta tables:

* Top 3 & Bottom 3 Sales (Store / Product)
* Inventory below threshold
* Store-wise delivery spend
* Daily profit trend

➡️ Dashboard samples:

* [Power BI Dashboards](./dashboards/README.md)

---

## 🎯 Key Engineering Highlights

* Delta Live Tables with APPLY CHANGES (SCD Type 2)
* Unity Catalog–based data governance
* Schema enforcement & data quality expectations
* Fault-tolerant orchestration with alerts
* Enterprise CI/CD with automated testing

---

## 📎 Who This Repository Is For

* Hiring Managers
* Data Engineering Interviewers
* Architects reviewing real-world Azure Databricks implementations

This repository focuses on **design decisions, architecture, and production practices**, not just code.

---

📌 **Next:** Open any pipeline link above to explore detailed architecture and flows.
