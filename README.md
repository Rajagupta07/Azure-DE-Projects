🚀 Real-Time Data Pipeline (Batch + Streaming) on Azure
📌 Project Overview
Designed and implemented an end-to-end hybrid data pipeline combining batch and real-time streaming processing using Azure services. The project follows Medallion Architecture (Bronze → Silver → Gold) with secure, production-level practices.

🎯 Objectives
Process both batch and streaming data in a unified architecture
Implement scalable and fault-tolerant pipelines
Apply secure authentication (OAuth + Key Vault)
Build modular and reusable Databricks notebooks
Generate business KPIs for analytics (Gold layer)


🏗️ Architecture

Batch Data (ADF)         Streaming Data (Event Hub)
        │                        │
        ▼                        ▼
        ──────── ADLS (Bronze Layer) ────────
                        │
                        ▼
              Databricks (Transformation)
                        │
                        ▼
        ──────── ADLS (Silver Layer) ────────
                        │
                        ▼
        ──────── ADLS + UC (Gold Layer) ────────

🧰 Tech Stack
Azure Data Factory (ADF)
Azure Event Hub
Azure Data Lake Storage Gen2 (ADLS)
Azure Databricks (PySpark)
Azure Stream Analytics
Azure Key Vault
Microsoft Entra ID (Service Principal)
Unity Catalog

For more Information pls refer docs/azure-realtime-data-pipeline.md