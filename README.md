# E-Commerce Sales Data Cleaner

This project focuses on building an *Extract, Transform, Load (ETL)* pipeline using *AWS Glue* to clean and enrich e-commerce sales data. The goal is to transform raw, inconsistent CSV files into clean, structured data stored in *Parquet format* on Amazon S3.

 ## Project Overview

Raw sales data often suffers from:
- Duplicate transactions
- Missing values (e.g., price, quantity)
- Inconsistent date formats

These issues affect data quality and make analysis difficult. This ETL pipeline resolves them using the following steps:

*Duplicate Removal*: Removes redundant order entries  
*Missing Value Handling*: Fills nulls in essential fields (e.g., quantity, price)  
*Date Standardization*: Converts all dates to a uniform format  
*Data Enrichment*: Joins with a product reference table using product_id  

---

## Project Files

This repository includes the following files:

1. *sales_data.csv* – Raw sales transactions (input)  
2. *product_data.csv* – Product metadata (used for joining) Includes product IDs, names, categories, etc 
3. *glue_etl_script.py* – ETL script in PySpark to clean and process the data  
 

---

## Technologies Used

- *Amazon S3* – Data storage  
- *AWS Glue* – ETL platform  
- *PySpark* – Transformation logic  
- *Parquet* – Optimized output format  

---

## Output

-run-1749471647631-part-r-00000 Description: This file is the output of the ETL job after processing
ecommerce-raw-data. It represents the cleaned and standardized customer data. Characteristics: Compared to the raw input, this file is expected to have: No duplicate rows. Fewer or no missing values in key fields (depending on the imputation strategy).Consistent formats order id ,product id and quantity. Uniform proper casing for price and total amount. Purpose: This file demonstrates the successful execution of the data cleaning pipeline and provides a ready-to-use dataset for analytics and other business applications. The timestamp in the filename is indicative of a specific Glue job run.





