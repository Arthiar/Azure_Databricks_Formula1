# Azure Databricks Formula 1 - Data Engineering

Data engineering projects built on Azure Databricks using the medallion architecture (Bronze → Silver → Gold). All projects process historical Formula 1 racing data (1950-2025).

## Projects

### 1. Formula 1 Project (Full Load)
A full-refresh pipeline — every run overwrites all tables from scratch.
- **Catalog:** `formula1`
- **Strategy:** Full overwrite every run
- **Job:** 17-task DAG on one cluster
- **Location:** `Databricks_Formula1_Project/Formula 1 Project/`

### 2. Formula 1 Incremental Overload
The production-ready version. Processes one batch at a time using Delta MERGE (upsert).
- **Catalog:** `formula1_incr`
- **Strategy:** Batch-by-batch, merge/upsert with control table
- **Location:** `Databricks_Formula1_Project/Formula 1 Incremental Overload/`

## Class-Based Refactoring

After building individual per-entity notebooks, I refactored Bronze and Silver into single-class implementations:

- **Bronze Class** (`07-Bronze class_optimised`) — One `BronzeIngestion` class with shared `_ingest()` pipeline
- **Silver Class** (`07-Silver_class`) — One `SilverTransformation` class with reusable helpers

## Tech Stack

- Azure Databricks (notebooks, jobs, SQL, dashboards)
- Unity Catalog
- Delta Lake
- PySpark
- Databricks Jobs (multi-task DAG)

## Author

**Arthisree Saraswathi Rajamanickam**
