# 🛍️ E-Commerce Sales Data Cleaner

This project is part of an internship assignment focused on cleaning raw e-commerce sales data using **AWS Glue** and **S3**, and saving the processed output in **Parquet format** for efficient analysis.

---

## 📌 Project Overview

**Objective**:  
Clean and transform raw CSV data containing sales transactions, remove inconsistencies, and enrich it by joining with product information.

---

## 📂 Input Data

- **Raw Sales CSV**  
  Path: `s3://ecommerce-data-bucket/raw/sales_data/`  
  Contains missing values, duplicates, and inconsistent date formats.

- **Product Reference CSV**  
  Path: `s3://ecommerce-data-bucket/raw/product_data/`  
  Includes product IDs, names, categories, etc.

---

## 🔧 ETL Process in AWS Glue

1. **Remove Duplicates**  
   → Using `.dropDuplicates()`

2. **Fill Null Values**  
   → `.fillna()` used to replace missing quantity and price fields

3. **Standardize Date Format**  
   → `to_date()` applied on `order_date` column

4. **Join with Product Table**  
   → `sales_data JOIN product_data ON product_id`

5. **Save to S3 in Parquet Format**  
   → Cleaned output: `s3://ecommerce-data-bucket/cleaned_data/`

---

## 📜 Technologies Used

- AWS S3
- AWS Glue (Jobs, Crawlers)
- PySpark
- Parquet Format
- IAM Roles for access management

---

## 🧾 Sample Glue Script (ETL)

```python
sales_df = sales_df.dropDuplicates()
sales_df = sales_df.fillna({'quantity': 0, 'price': 0})
sales_df = sales_df.withColumn("order_date", to_date(col("order_date"), "yyyy-MM-dd"))
joined_df = sales_df.join(product_df, on="product_id", how="left")
```

---

## ✅ Output

- Cleaned sales data available in:  
  `s3://ecommerce-data-bucket/cleaned_data/`
- Format: **Parquet** (faster querying + storage optimized)

---

## 📊 Optional Add-ons

- Query using **Amazon Athena**
- Visualize using **Amazon QuickSight**

---

## 🙋‍♂️ Author

**Mayur Koli**  
Intern – AWS Data Engineering Project

---

## 📅 Last Updated

June 11, 2025
