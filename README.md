🏛️ Data Warehouse on Medallion Architecture
📌 Overview

This project demonstrates a Data Warehouse built using the Medallion Architecture layered approach (Bronze → Silver → Gold) on Massively Parallel Processing (MPP) systems with SQL Server PDW / Azure Synapse.

It simulates real-world ETL flows, enforces data quality checks, and leverages star schema modeling for analytics.

⚡ Key Features

Layered Medallion Architecture:

Bronze → Raw ingestion from CRM & ERP sources

Silver → Cleansed and standardized data

Gold → Curated star schema for BI & reporting

Data Quality Checks implemented at Silver and Gold stages.

Scalable Queries using MPP parallelism in Synapse/PDW.

ETL Simulation with SQL-based stored procedures.

📂 Repository Structure
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

🚀 Workflow (Medallion Layers)

Bronze Layer

Ingests raw data from multiple sources (CRM, ERP).

Scripts: ddl_bronze.sql, proc_load_bronze.sql.

Silver Layer

Cleanses, standardizes, and enriches data.

Scripts: ddl_silver.sql, proc_load_silver.sql.

Quality checks: quality_checks_silver.sql.

Gold Layer

Curates analytical-ready Star Schema with Fact & Dimension tables.

Scripts: ddl_gold.sql.

Quality checks: quality_checks_gold.sql.

📊 Example Query
SELECT d.Year, p.Category, SUM(f.SalesAmount) AS TotalSales
FROM FactSales f
JOIN DimDate d ON f.DateKey = d.DateKey
JOIN DimProduct p ON f.ProductKey = p.ProductKey
GROUP BY d.Year, p.Category;

✅ Data Quality

Ensures referential integrity between Fact & Dimension tables.

Validates data completeness and uniqueness.

Checks for duplicate records and null values.

🛠️ Tech Stack

SQL Server PDW / Azure Synapse Analytics (MPP Engine)

Star Schema Modeling (Fact & Dimension tables)

SQL-based ETL (stored procedures, transformations, quality checks)

📖 Learnings

Medallion-based architectures improve scalability & data governance.

MPP queries provide massive performance gains over traditional warehouses.

Data quality enforcement is key to trustworthy analytics.

🤝 Contributing

Contributions are welcome! Please fork the repo, create a feature branch, and submit a pull request.

📜 License

This project is licensed under the MIT License.
