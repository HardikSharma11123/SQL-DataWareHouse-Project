# 🏗️ SQL Data Warehouse Project
## Medallion Architecture Implementation (Bronze → Silver → Gold)


## 📌 Overview

This project implements a **production-ready SQL Data Warehouse** using the **Medallion Architecture** pattern to ingest, transform, and model data for enterprise analytics and reporting. Built with SQL Server, it demonstrates industry-standard data engineering practices including layered data processing, comprehensive data quality management, and dimensional modeling.

### 🎯 Key Features

- ✅ **Three-tier medallion architecture** for progressive data refinement
- ✅ **Automated ETL pipelines** using T-SQL stored procedures
- ✅ **Data quality validation** and error handling mechanisms
- ✅ **Star schema dimensional modeling** for optimal query performance
- ✅ **Incremental load patterns** for efficient data processing
- ✅ **Comprehensive documentation** with architecture diagrams

---

## 🧠 Architecture Overview

The solution implements a **three-layer Medallion Architecture**, a design pattern that organizes data processing into bronze, silver, and gold layers for improved data quality and governance.

### 🔹 Bronze Layer (Raw Data Zone)
```
Purpose: Historical landing zone for immutable source data
```
- Ingests raw, unprocessed data from source systems
- Maintains complete data lineage and audit trail
- Schema-on-read approach with minimal constraints
- Supports full and incremental loads
- **No transformations or business logic applied**

### 🔹 Silver Layer (Curated Data Zone)
```
Purpose: Cleaned, validated, and enriched enterprise data
```
- Data cleansing and standardization
- Duplicate detection and handling
- Data type conversions and formatting
- Reference data integration
- Slowly Changing Dimension (SCD) implementation
- Business rule validation

### 🔹 Gold Layer (Consumption-Ready Zone)
```
Purpose: Analytics-optimized data models for business intelligence
```
- Star schema dimensional models (Facts & Dimensions)
- Pre-aggregated summary tables
- Business-friendly column naming
- Optimized for query performance
- Ready for BI tools and reporting

---

## 🖼️ Data Flow Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      SOURCE SYSTEMS                         │
│         CRM  •  ERP  •  CSV Files  •  APIs                 │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   🟤 BRONZE LAYER                           │
│              Raw_Customers | Raw_Orders                     │
│              Raw_Products  | Raw_Transactions                │
│                                                              │
│  Strategy: Full Load / Incremental                          │
│  Format: As-is from source (immutable)                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   ⚪ SILVER LAYER                           │
│           Cleaned_Customers | Cleaned_Orders                │
│           Cleaned_Products  | Cleaned_Transactions          │
│                                                              │
│  Transformations:                                           │
│  • Data Quality Checks                                      │
│  • Deduplication                                            │
│  • Standardization                                          │
│  • Enrichment                                               │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   🟡 GOLD LAYER                             │
│         Dim_Customer | Dim_Product | Dim_Date               │
│         Fact_Sales   | Fact_Inventory                       │
│                                                              │
│  Models:                                                    │
│  • Star Schema                                              │
│  • Aggregate Tables                                         │
│  • Business Metrics                                         │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              📊 CONSUMPTION LAYER                           │
│    Power BI  •  Tableau  •  Excel  •  SQL Queries          │
│    ML Models  •  APIs  •  Reports                          │
└─────────────────────────────────────────────────────────────┘
```



## ⚙️ Technology Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Database Engine** | SQL Server 2019+ | Data storage and processing |
| **Query Language** | T-SQL | ETL logic and transformations |
| **Architecture Pattern** | Medallion (Bronze-Silver-Gold) | Data organization |
| **Data Modeling** | Star Schema | Dimensional modeling |
| **Version Control** | Git & GitHub | Code management |
| **Documentation** | Markdown | Technical documentation |

---

## 🚀 Getting Started

### Prerequisites

- SQL Server 2019 or later
- SQL Server Management Studio (SSMS) or Azure Data Studio
- Basic understanding of T-SQL and data warehousing concepts

### Installation Steps

1. **Clone the repository**
```bash
git clone https://github.com/HardikSharma11123/SQL-DataWareHouse-Project.git
cd SQL-DataWareHouse-Project
```

2. **Create the database**
```sql
CREATE DATABASE DataWarehouse;
GO

USE DataWarehouse;
GO
```

3. **Execute scripts in order**

```sql
-- Step 1: Bronze Layer Setup
:r scripts/bronze/01_create_bronze_tables.sql
:r scripts/bronze/02_load_customers.sql
:r scripts/bronze/03_load_orders.sql

-- Step 2: Silver Layer Setup
:r scripts/silver/01_create_silver_tables.sql
:r scripts/silver/02_transform_customers.sql
:r scripts/silver/03_transform_orders.sql

-- Step 3: Gold Layer Setup
:r scripts/gold/01_create_dimensions.sql
:r scripts/gold/02_create_facts.sql
:r scripts/gold/03_create_analytics_views.sql
```

4. **Verify installation**
```sql
-- Run test queries
SELECT COUNT(*) AS BronzeRowCount FROM Bronze.Raw_Customers;
SELECT COUNT(*) AS SilverRowCount FROM Silver.Cleaned_Customers;
SELECT COUNT(*) AS GoldRowCount FROM Gold.Dim_Customer;
```

---

## 📊 Use Cases & Applications

### Business Intelligence
- Executive dashboards showing KPIs and trends
- Sales performance analysis by region, product, and time
- Customer segmentation and behavior analytics

### Operational Reporting
- Daily sales reports
- Inventory status monitoring
- Order fulfillment tracking

### Advanced Analytics
- Predictive modeling data preparation
- Cohort analysis
- Trend analysis and forecasting
- Customer lifetime value calculation

### Ad-Hoc Analysis
- Self-service BI for business users
- Data exploration and discovery
- Custom report generation

---


<div align="center">

**⭐ If you find this project helpful, please give it a star!**

</div>
