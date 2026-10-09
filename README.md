# Azure Databricks & Microsoft Fabric Medallion Lakehouse

End-to-end data pipeline built on Azure Databricks, Delta Lake, and Microsoft Fabric to process e-commerce transaction data using Medallion Architecture.

---

## Architecture Flow

Raw JSON/CSV Data ➔ Azure Databricks (Bronze Ingestion) ➔ Silver Cleansing & Quality Checks ➔ Gold Business Aggregations ➔ Microsoft Fabric Lakehouse ➔ Power BI (Direct Lake)

1. **Bronze Layer**: Raw data ingestion with initial schema validation, saved as Delta Parquet format.
2. **Silver Layer**: Data cleaning, null handling, deduplication, and schema enforcement.
3. **Gold Layer**: Aggregated business metrics (customer LTV, product sales trends, order rollups) structured for reporting.
4. **Reporting**: Microsoft Fabric integration via Direct Lake for real-time reporting without manual dataset refreshes.

---

## Directory Layout

```text
.
├── notebooks/
│   ├── 01_bronze_ingestion.py        # Raw data load & schema validation
│   ├── 02_silver_transformation.py  # Cleansing, deduplication & quality checks
│   └── 03_gold_transformation.py    # Metric calculation & dimension modeling
├── orchestration/
│   └── databricks_workflow_job.json # Databricks Workflow job definition (IaC)
├── assets/
│   ├── databricks_workflow_dag.png   # Job execution run screenshot
│   ├── powerbi_dashboard.png         # Power BI report screenshot
│   └── adls_delta_storage.png        # Delta Lake containers in ADLS Gen2
├── .gitignore
└── README.md
