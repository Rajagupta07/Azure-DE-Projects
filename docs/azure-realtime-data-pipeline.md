 Implementation Details

🔹 1. Batch Pipeline (ADF)
Created dynamic pipelines using parameterized datasets
Ingested CSV data into ADLS Bronze layer
Used Copy Activity with dynamic file paths

🔹 2. Streaming Pipeline
Created Event Hub for real-time ingestion
Simulated streaming data using Python producer
Processed data via Stream Analytics
Stored output in ADLS Bronze

🔹 3. Data Lake (Bronze Layer)
Stored raw data in:
/data-lake/bronze/batch/
/data-lake/bronze/stream/

🔹 4. Security (Production-Level)
Created Service Principal for authentication
Stored credentials in Azure Key Vault
Integrated Key Vault with Databricks (Secret Scope)
Used OAuth authentication (no hardcoded secrets)

RBAC Roles:
Storage Blob Data Contributor
Key Vault Secrets User

🔹 5. Databricks Project Structure
workspace/
│
├── common/
│   ├── 01_config
│   ├── 02_adls_connection
│
├── batch/
│   └── bronze_to_silver_batch
│
├── stream/
│   └── bronze_to_silver_stream
│
├── gold/
│   ├── silver_to_gold_batch
│   ├── silver_to_gold_stream
│   └── create_gold_tables
│
├── setup/
│   └── create_tables


🔹 6. Bronze → Silver Transformation
Batch:
Removed nulls & duplicates
Type casting
Data standardization
Derived column: TotalAmount
Streaming:
Cleaned JSON data
Removed invalid records
Converted timestamps
Dropped unused columns (revenue, total_orders)
Stored as:
ADLS (Delta format)
/silver/batch/
/silver/stream/

🔹 7. Silver → Gold Transformation
Batch KPIs:
Total Revenue
Revenue by Country
Top Customers
Daily Sales

Streaming KPIs:
Orders per City
Revenue per City
Real-time Summary

🔹 8. Gold Layer Storage
Stored as Delta files in ADLS:
/data-lake/gold/batch/
/data-lake/gold/stream/

Also registered as Unity Catalog tables

🔹 9. Unity Catalog Integration
Created catalog & schema
Created managed/external tables
Queried Gold data using SQL

🔹 10. Validation
Verified record counts
Validated schema
Queried tables using SQL

🔹 11. CI/CD & Version Control
Structured notebooks for modularity
Prepared project for GitHub integration

Ready for deployment using:
GitHub Actions / Azure DevOps
Databricks Jobs

📊 Key Features
Hybrid pipeline (Batch + Streaming)
Medallion Architecture implementation
Secure secret management (Key Vault)
Modular notebook design (%run)
Delta Lake usage for reliability
Unity Catalog integration
ADLS-based storage for all layers

🚨 Challenges & Solutions
Issue	Solution
Key Vault access error	Assigned RBAC roles
ADLS permission error	Added Storage Blob Data Contributor
Secret scope creation issue	Used Databricks UI endpoint
Unity Catalog restrictions	Used managed tables
Storage key conflict	Switched to OAuth configuration

🧠 Key Learnings
Difference between Batch vs Streaming pipelines
Importance of RBAC and secure access
Databricks modular design using %run
Unity Catalog vs Hive Metastore
Medallion Architecture in real projects

