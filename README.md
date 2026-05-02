# Azure-DE-Projects

01_Bronze_To_Silver
In the Bronze layer, I stored raw batch and streaming data as received from ADF and Event Hub. In Databricks, I transformed Bronze data into Silver by applying schema enforcement, null handling, deduplication, type casting, standardization, and business validations. Finally, I stored the cleaned data in Delta format for reliable downstream analytics.