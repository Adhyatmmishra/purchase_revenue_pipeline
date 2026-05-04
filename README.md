🚀 End-to-End Data Pipeline on Databricks (Medallion Architecture)

📌 Overview :- 
This project demonstrates a production-style data engineering pipeline built using the Medallion Architecture (Bronze → Silver → Gold) on Databricks.
The pipeline processes retail domain data (dummy dataset) and transforms it into analytics-ready insights, simulating a real-world data platform.

🏗️ Architecture
Flow:
Raw JSON → Bronze → Silver → Gold → BI / Analytics

🎯 Objectives
Build a scalable ETL pipeline using Databricks
Implement data quality checks and validation
Design layered architecture for better data governance
Generate business-level insights from raw data

🗂️ Storage Layer

Since this project uses dummy retail data, the storage layer is implemented using:

✅ Databricks Volumes (used in this project)

💡 In real-world production systems, this can be replaced with:

AWS S3
Azure Data Lake Storage (ADLS)


🔄 Pipeline Workflow
🔹 1. Raw → Bronze (Ingestion Layer)

Purpose: Ingest raw data with minimal transformation
Read raw JSON files from Databricks Volumes
Add ingestion metadata (timestamp, source info)
Extract load_date from file path
Store raw data into Bronze Delta Tables

🔹 2. Bronze → Silver (Transformation Layer)
Purpose: Clean, validate, and enrich data
Apply data quality checks on orders
Separate valid and rejected records
Fix timestamp parsing issues
Clean & deduplicate product master data
Enrich orders with product details
Store curated and rejected datasets in Silver Delta Tables

🔹 3. Silver → Gold (Business Layer)
Purpose: Create analytics-ready datasets
Apply business/safety filters
Generate daily product sales metrics
Generate category-level sales insights
Store results in Gold Delta Tables


🔄 Orchestration
Used Databricks Lakeflow for:
Pipeline orchestration
Job scheduling
Workflow management
Failure handling & retries
