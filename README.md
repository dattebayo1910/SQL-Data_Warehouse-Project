🏛️ Data Warehouse on Medallion Architecture
📌 Overview

This project demonstrates the design and implementation of a scalable Data Warehouse built on the Medallion Architecture using Massively Parallel Processing (MPP) with SQL Server PDW/Synapse.

The solution is designed to handle large-scale analytics workloads, showcasing efficient data modeling, ETL flows, and querying strategies.

⚡ Key Highlights

Medallion Architecture: Implemented a layered data approach (Bronze, Silver, Gold) for structured and incremental data refinement.

Scalable MPP System: Leveraged Madison (MPP) architecture for high-performance distributed query execution.

Data Modeling: Designed Star Schema with Fact and Dimension tables to optimize analytical queries.

Parallel Querying: Used SQL Server PDW/Synapse for distributed queries across compute nodes.

ETL Simulation: Implemented data loading and transformation logic to mimic real-world ETL pipelines.

🛠️ Tech Stack

Data Warehouse Platform: SQL Server PDW / Azure Synapse Analytics

Architecture: Medallion (Bronze → Silver → Gold layers)

Modeling: Star Schema (Fact + Dimension tables)

ETL: SQL-based transformations & loading logic

Query Engine: MPP for distributed parallel queries

📂 Project Structure
├── datasets/
│   ├── source_crm/             # CRM source data samples
│   ├── source_erp/             # ERP source data samples
│
├── docs/                       # Documentation & diagrams
│
├── scripts/
│   ├── bronze/
│   │   ├── ddl_bronze.sql      # DDL for Bronze layer tables
│   │   ├── proc_load_bronze.sql # Procedures to load raw data
│   │
│   ├── silver/
│   │   ├── ddl_silver.sql      # DDL for Silver layer tables
│   │   ├── proc_load_silver.sql # Transformation & loading
│   │
│   ├── gold/
│   │   ├── ddl_gold.sql        # DDL for Gold (Star Schema) tables
│   │
│   ├── tests/
│   │   ├── quality_checks_silver.sql # Data quality checks for Silver
│   │   ├── quality_checks_gold.sql   # Data quality checks for Gold
│   │
│   ├── init_database.sql       # Initialize schemas & environment
│
└── README.md


🚀 How It Works

Bronze Layer: Load raw data into staging tables.

Silver Layer: Apply transformation logic to clean, normalize, and enrich data.

Gold Layer: Curate analytical data models in a Star Schema for business intelligence use cases.

Query Execution: Run distributed queries on Synapse/PDW leveraging parallelism for faster results.

📊 Example Use Case

Fact Table: FactSales – stores transactional sales data.

Dimension Tables: DimCustomer, DimProduct, DimDate, DimStore.

Example Query:

SELECT d.Year, p.Category, SUM(f.SalesAmount) AS TotalSales
FROM FactSales f
JOIN DimDate d ON f.DateKey = d.DateKey
JOIN DimProduct p ON f.ProductKey = p.ProductKey
GROUP BY d.Year, p.Category;

📖 Learnings

Designing Medallion-based architectures improves scalability & maintainability.

MPP architectures like Madison enable high-performance query execution.

Star schemas remain one of the most effective models for analytical queries.

Simulated ETL pipelines help in understanding real-world data flows.

🤝 Contributing

Contributions are welcome! Please fork the repo, create a feature branch, and submit a pull request.

📜 License

This project is licensed under the MIT License.
