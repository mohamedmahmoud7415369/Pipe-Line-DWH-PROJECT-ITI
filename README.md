# DWH-PROJECTS-ITI
Of course. Here is a professionally crafted README.md designed to attract recruiters and showcase your skills. It's structured to be comprehensive, visually appealing, and keyword-rich for both human readers and automated tracking systems.

Copy and paste the content below into a `README.md` file in your `DWH-PROJECTS-ITI` repository.

---

# Enterprise Data Warehouse Portfolio 🚀

[![Azure](https://img.shields.io/badge/Azure-Cloud%20Services-0078D4?logo=microsoftazure)](https://azure.microsoft.com/)
[![Snowflake](https://img.shields.io/badge/Snowflake-Data%20Warehouse-29B5E8?logo=snowflake)](https://www.snowflake.com/)
[![dbt](https://img.shields.io/badge/dbt-Data%20Transformation-FF694B?logo=dbt)](https://www.getdbt.com/)
[![Airflow](https://img.shields.io/badge/Airflow-Workflow%20Orchestration-017CEE?logo=apacheairflow)](https://airflow.apache.org/)
[![SQL Server](https://img.shields.io/badge/SQL%20Server-Database-CC2927?logo=microsoftsqlserver)](https://www.microsoft.com/sql-server/)
[![Power BI](https://img.shields.io/badge/Power_BI-Visualization-F2C811?logo=powerbi)](https://powerbi.microsoft.com/)

A curated collection of end-to-end Data Warehouse projects built with modern cloud technologies. This portfolio demonstrates the complete lifecycle of data from ingestion to insightful reporting, implementing robust data architecture patterns like the **Medallion Architecture**.

## 🏗️ Architecture & Philosophy

This portfolio champions the **Modern Data Stack**, leveraging best-of-breed, cloud-native tools for scalability, reliability, and maintainability. The core design pattern across all projects is the **Medallion Architecture**, ensuring incremental data quality and governance.

### End-to-End Pipeline Architecture
```mermaid
flowchart TD
    /* Data Sources */
    A[SQL Server<br>OLTP Database] -->|Azure Data Factory| B
    C[Azure Blob Storage<br>CSV/JSON Files] -->|Azure Data Factory| B
    D[Simulated SaaS API] -->|Azure Data Factory| B

    subgraph "Modern Data Stack Pipeline"
        B[("Azure Data Lake Gen2<br>Bronze Layer Raw Data")]
        B --> E[Apache Airflow<br>Orchestrator]
        E --> F["dbt Cloud<br>Transformation Layer"]
        B -.->|Reads| F

        subgraph "Snowflake Data Platform"
            G[("BRONZE<br>Raw/Staging")]
            H[("SILVER<br>Cleaned & Integrated")]
            I[("GOLD<br>Business Marts & KPIs")]
        end

        F -->|Models & Tests| G
        F -->|Models & Tests| H
        F -->|Models & Tests| I
    end

    I --> J["Power BI<br>Dashboards"]
    I --> K[Ad-hoc Analysis]
    I --> L[Data Science]

    E --> M["Data Lineage &<br>Quality Monitoring"]
```

### The Medallion Architecture In Practice

```mermaid
flowchart LR
    S[Source Systems] -->|ELT| Bronze

    subgraph "Medallion Data Layers"
        Bronze[("🟤 BRONZE<br>Raw & Immutable")]
        Bronze --> T1["Type Casting<br>Basic Cleansing"]
        T1 --> Silver[("⚪ SILVER<br>Cleaned & Conformed"])
        Silver --> T2["Business Logic<br>Aggregations<br>Dimensional Modeling"]
        T2 --> Gold[("🟡 GOLD<br>Business-ready Marts"])
    end

    Gold --> C[Consumption]

    classDef bronze fill:#8C5A19,color:white;
    classDef silver fill:#B4B4B4,color:black;
    classDef gold fill:#FFD700,color:black;
    classDef consumption fill:#4CAF50,color:white;

    class Bronze bronze;
    class Silver silver;
    class Gold gold;
```

*   **🟤 Bronze Layer:** The landing zone. Raw data is ingested in its original format, ensuring immutability and historical traceability. *(Tools: Azure Data Factory, ADLS Gen2)*
*   **⚪ Silver Layer:** The single source of truth. Raw data is cleansed, standardized, deduplicated, and integrated into a structured, query-ready format (often a Data Vault or 3NF model). *(Tools: dbt, Snowflake)*
*   **🟡 Gold Layer:** The consumption layer. Data is transformed into business-intuitive dimensional models (Star Schema) or highly aggregated datasets optimized for specific analytics and reporting needs. *(Tools: dbt, Snowflake)*

## ⚙️ Technology Stack

| Layer | Technology | Purpose & Justification |
| :--- | :--- | :--- |
| **Ingestion & Orchestration** | **Azure Data Factory**, **Apache Airflow** | Building scalable, fault-tolerant ELT pipelines with robust scheduling and monitoring. |
| **Cloud Storage** | **Azure Data Lake Storage (ADLS) Gen2** | Cost-effective, highly available storage for raw and processed data in open formats (Parquet, Delta). |
| **Data Warehouse** | **Snowflake** | The core analytical database. Leveraged its separation of compute/storage, zero-copy cloning, and time travel for efficient development and testing. |
| **Transformation & Modeling** | **dbt (Data Build Tool)** | Applied software engineering practices (version control, modularity, testing) to data transformation. Built documented, maintainable, and tested SQL models. |
| **Source Database** | **Microsoft SQL Server** | Simulated enterprise-grade transactional systems as data sources. |
| **Visualization** | **Power BI** | Developed interactive dashboards to deliver actionable insights from the Gold layer data models. |
| **Version Control** | **Git** | All code is version-controlled, demonstrating collaboration and CI/CD readiness. |

## 📂 Project Showcase

### Project 1: E-Commerce Sales Analytics Dashboard
**Objective:** Build a centralized data platform to analyze sales performance, customer behavior, and product trends.
*   **Sources:** SQL Server (Orders, Customers), CSV (Product Catalog), API (Shipping Data)
*   **Key Models:** `fct_orders`, `dim_customers`, `dim_products`, `dim_date`
*   **Transformations:** SCD Type 2 for customer attributes, revenue calculations, geographic enrichment.
*   **Outcome:** A Power BI dashboard providing views into YTD revenue, sales by region, and customer cohorts.

### Project 2: Telecom Customer Churn Prediction Pipeline
**Objective:** Create a curated dataset for a machine learning model to predict customer churn.
*   **Sources:** REST API (Customer Profiles), Parquet Files (Call Detail Records), SQL Server (Billing)
*   **Key Models:** `fct_customer_interactions`, `dim_customer_status`, aggregated features like `avg_monthly_spend`.
*   **Transformations:** Complex window functions for rolling aggregates, data quality tests to handle missing CDR records.
*   **Outcome:** A clean, feature-rich Gold layer table served to Databricks for model training.

## 🎯 Key Competencies Demonstrated

*   **End-to-End Pipeline Development:** Proven ability to own the entire data lifecycle, from source systems to production-ready dashboards.
*   **Cloud Data Engineering:** Hands-on expertise with major cloud providers (Azure) and SaaS platforms (Snowflake).
*   **Modern Data Stack Proficiency:** Deep practical knowledge of the industry's leading tools (ADF, dbt, Airflow, Snowflake).
*   **Data Modeling:** Designed and implemented both normalized (Silver) and dimensional (Gold) data models for optimal performance and usability.
*   **Data Quality & Reliability:** Engineered pipelines with built-in data validation, testing (using dbt tests), and monitoring for proactive issue detection.
*   **Infrastructure as Code (IaC):** Managed data warehouse schemas and transformation logic through version-controlled code (SQL, YAML, Python).

---

**Author:** [Your Name] | Data Engineering Graduate, ITI ICC
**LinkedIn:** [Your LinkedIn Profile URL]
**Portfolio:** [Your Personal Portfolio URL]
