# Data Warehouse and Analytics Project

## Overview

This project demonstrates the design and implementation of an end-to-end Data Warehouse using SQL Server and the Medallion Architecture (Bronze, Silver, Gold). It integrates CRM and ERP datasets, applies data cleansing and transformation processes, and delivers a business-ready analytical model based on a Star Schema.

The project follows modern Data Engineering principles, including layered architecture, Separation of Concerns (SoC), dimensional modeling, and data quality validation.

---

## Project Highlights

- End-to-End Data Warehouse implementation
- Medallion Architecture (Bronze, Silver, Gold)
- ETL pipelines using SQL Server
- CRM & ERP data integration
- Data Lineage and Integration Model documentation
- Star Schema dimensional model
- Data Quality validation scripts

## Architecture

The solution follows the Medallion Architecture:

```
                Source Systems
               CRM        ERP
                   │
                   ▼
            Bronze Layer
          (Raw Data Ingestion)
                   │
                   ▼
            Silver Layer
    (Data Cleansing & Integration)
                   │
                   ▼
             Gold Layer
      (Star Schema & Analytics)
```

---

## Repository Structure

```text
datasets/
│
├── source_crm/
│   ├── cust_info.csv
│   ├── prd_info.csv
│   └── sales_details.csv
│
├── source_erp/
│   ├── CUST_AZ12.csv
│   ├── LOC_A101.csv
│   └── PX_CAT_G1V2.csv

docs/
│
├── data_flow.png
├── data_integration.png
└── data_model.png

scripts/
│
├── bronze/
│   ├── bronze_schema.sql
│   └── bronze_ingestion.sql
│
├── silver/
│   ├── silver_schema.sql
│   └── silver_transformations.sql
│
├── gold/
│   ├── dimensions/
│   │   ├── dim_customers.sql
│   │   └── dim_products.sql
│   │
│   └── facts/
│       └── fact_sales.sql
│
└── init_database.sql

tests/
│
├── quality_checks_silver.sql
└── quality_checks_gold.sql
```

---

# Data Sources

The project integrates data from two operational systems:

### CRM

- Customer Information
- Product Information
- Sales Transactions

### ERP

- Customer Demographics
- Customer Locations
- Product Categories

---

# Bronze Layer

The Bronze layer stores raw data exactly as received from the source systems.

Responsibilities:

- Create raw tables
- Load CSV files using BULK INSERT
- Preserve original data
- No transformations applied

---

# Silver Layer

The Silver layer performs data cleansing and standardization.

Responsibilities:

- Remove duplicate records
- Standardize values
- Clean invalid data
- Apply business rules
- Integrate CRM and ERP datasets

---

# Gold Layer

The Gold layer exposes business-ready datasets using a dimensional model.

Objects:

- dim_customers
- dim_products
- fact_sales

The analytical model follows a Star Schema to support reporting and business intelligence workloads.

---

# Data Modeling

The Gold layer implements a Star Schema consisting of:

- Customer Dimension
- Product Dimension
- Sales Fact Table

Surrogate keys are generated for all dimensions to support analytical processing.

---

# Documentation

The project includes additional documentation describing the overall architecture.

- Data Flow Diagram
- Data Integration Model
- Star Schema Model

These diagrams are available under the **docs/** folder.

---

# Data Quality Validation

Validation scripts are included to verify:

- Duplicate surrogate keys
- Referential integrity
- Dimension-to-fact relationships
- Gold layer consistency

---

# Technologies

- SQL Server
- T-SQL
- Medallion Architecture
- ETL
- Data Warehousing
- Star Schema
- Data Modeling

---

# Key Concepts

- Medallion Architecture
- Separation of Concerns
- ETL Pipelines
- Data Cleansing
- Data Integration
- Data Lineage
- Dimensional Modeling
- Star Schema
- Surrogate Keys
- Data Quality Validation

---

# Future Improvements

Possible extensions include:

- Incremental loading
- Change Data Capture (CDC)
- Logging and monitoring
- SQL Server Agent scheduling
- Power BI dashboards
- Azure Data Factory
- Databricks implementation
