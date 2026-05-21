# 🛒 Superstore End-to-End Analytics Pipeline

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=for-the-badge&logo=duckdb&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

## 📌 Project Overview
This repository contains an automated end-to-end data pipeline built for a retail Superstore. It takes raw transactional data, performs data cleaning and feature engineering, loads it into an in-memory OLAP database (**DuckDB**), executes advanced SQL aggregations, and generates both a static executive dashboard and a structured Excel file optimized for **Power BI** ingestion.

## ⚙️ The Pipeline Architecture
1. **Extract & Transform (Pandas):** - Standardized column naming conventions (snake_case).
   - Datetime parsing and duration calculations (e.g., `ship_days`).
   - Feature engineering: Categorizing discount thresholds, profit margins, and profit bands.
2. **Load & Query (DuckDB):** - Instant conversion of Pandas DataFrames into highly optimized SQL tables.
   - Execution of 9 specific analytical aggregations including YoY Growth, Category Performance, and Geo-mapping data.
   - Advanced SQL modeling: Root Cause Analysis (RCA) for Loss-Making Orders and RFM-style Customer Value segmentation.
3. **Export Semantic Layer:**
   - Outputs a multi-sheet `.xlsx` file (`superstore_powerbi_full.xlsx`) containing both the cleaned Fact Table and all aggregated Dimension tables, ready to be consumed by Power BI.

## 📊 Executive Dashboard Preview
![Dashboard Preview](output/dashboard.png)

## 💡 Key Business Insights
* **The Discounting Trap:** Discounts exceeding 20% severely erode profit margins, directly causing the majority of loss-making transactions, particularly in the Furniture category.
* **Cash Cow Segments:** The 'Home Office' segment yields the highest profit margin per customer, despite having a lower overall sales volume compared to the 'Consumer' segment.
* **Operational Bottlenecks:** Certain shipping modes correlate with lower margins, indicating a need to optimize logistics routing.

## 📂 Repository Structure
```text
superstore-analytics-pipeline/
│
├── data/
│   ├── raw/                 <- raw CSV file here
│   └── processed/           <- Cleaned CSV and DuckDB database 
│
├── output/                  <- Dashboard PNG and Power BI Excel file 
│
├── src/
│   └── pipeline.py          <- Main Python execution script
│
├── .gitignore
├── requirements.txt
└── README.md
