# ecommerce_01-databricks-assignment_02
E-commerce Data Engineering Lakehouse
1. Project Overview
This project implements an end-to-end e-commerce data engineering pipeline using Azure Databricks, PySpark, Unity Catalog, and Delta Lake.

The pipeline processes the Brazilian Olist e-commerce_01 dataset through Bronze, Silver, and Gold layers and includes Slowly Changing Dimension Type 2 (SCD Type 2), data quality validation, Delta Lake Time Travel, and notebook orchestration.

2. Technologies Used
Azure Databricks
Python and PySpark
SQL
Unity Catalog
Delta Lake
GitHub
3. Project Architecture
Bronze Layer
Reads five Olist CSV datasets.
Converts raw data to Parquet format.
Stores the processed data in the Bronze layer.
Silver Layer
Cleans and prepares the datasets.
Creates Delta tables for orders, order items, customers, products, and payments.
Gold Layer
Creates customer and product dimension tables.
Creates the order sales fact table.
Generates sales aggregations by state, product, day, and month.
SCD Type 2
Implements historical tracking for customer and product dimensions.
Uses effective dates and a current-record flag.
Master Pipeline
Runs Bronze, Silver, Gold, and both SCD Type 2 notebook executions in sequence.
Uses dbutils.notebook.run() for orchestration.
Includes error handling and execution status messages.
4. Main Notebooks
Notebook	Purpose
Volume_Setup	Volume and project setup
Bronze_Layer	CSV-to-Parquet processing
Silver_Layer	Data cleaning and Delta tables
Gold_Layer	Fact, dimension, and aggregation tables
SCD_Type2	Customer and product history
Master_Pipeline	End-to-end orchestration
5. Validation Results
The completed pipeline produced the following record counts:

Table or dataset	Rows
Bronze orders	99,441
Bronze order items	112,650
Bronze customers	99,441
Bronze products	32,951
Bronze order payments	103,886
Gold fact sales	112,650
Gold sales by state	27
Gold daily sales	616
Gold monthly sales	24
Data quality checks were completed for missing keys, duplicate order-item combinations, null revenue, and negative revenue.

6. Delta Lake Features
The project demonstrates:

Delta table history
Time Travel queries
A rollback exercise using a test table
7. Execution
The master pipeline was successfully executed in Azure Databricks, including Bronze, Silver, Gold, SCD Type 2 Customers, and SCD Type 2 Products.

A Databricks Job was also run successfully using Serverless compute.

8. Prerequisites
An Azure Databricks workspace
Access to Unity Catalog
A catalog, schema, and volume configured for the project
The required Olist CSV datasets
Permission to create and modify the project tables
9. How to Run
Configure the catalog, schema, and volume paths for your workspace.
Upload the required raw datasets.
Run the setup notebook if required.
Run the Bronze notebook.
Run the Silver notebook.
Run the Gold notebook.
Run the SCD Type 2 notebook for customers and products.
Run the master pipeline to orchestrate the complete workflow.
Review notebook parameters and workspace-specific paths before execution.

10. Data Source
Brazilian Olist e-commerce public dataset.

11. Notes
This project was developed for learning and assignment purposes. Table names, paths, permissions, and compute settings may need to be adjusted for another Databricks workspace.
