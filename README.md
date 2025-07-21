# ADF-Truncate-Load-Pipeline
# Azure Data Factory - Truncate Load Pipeline

This project implements a Truncate Load mechanism in Azure Data Factory for the following files:

1. CUST_MSTR_*.csv → dbo.CUST_MSTR
2. master_child_export-*.csv → dbo.MASTER_CHILD_EXPORT
3. H_ECOM_ORDER.csv → dbo.H_ECOM_ORDER

## 💻 Components

- Pipelines:
  - pipeline_truncate_load: Controls the truncate and load process.

- Dataflows:
  - df_CUST_MSTR
  - df_MASTER_CHILD_EXPORT
  - df_H_ECOM_ORDER

- Datasets:
  - Source: Binary/DelimitedText from ADLS
  - Sink: Azure SQL Table datasets

- Linked Services:
  - Azure Blob Storage
  - Azure SQL Database

## 🛠 How It Works

- Files are read from ADLS Gen2 using binary dataset
- Filename used to extract date via Derived Column
- Data flows used to map and transform data
- Sink is configured to truncate table and then load data
- Pipeline runs sequentially (no loop)

## ✅ Notes

- The fileDate is extracted using substring or hardcoded using currentUTC() where filename has no date.
- Truncate option is selected in Sink under "Pre-copy script" or table option.
- Debug run tested and successful for all 3 files.

## 📌 Author
Kashish Aggarwal
