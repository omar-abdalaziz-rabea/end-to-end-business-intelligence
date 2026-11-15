📊 End-to-End Data Cleaning, Transformation, Modeling | Power BI

📌 Project Overview

Designed and implemented a structured data transformation and modeling workflow to convert raw, inconsistent data into a clean, reliable, and analysis-ready dataset.

The project focuses on data quality, business rule enforcement, Star Schema design, and maintainable DAX measures to support accurate and efficient business reporting.

---

🎯 Key Objectives

- 🧹 Perform data cleaning using Power Query to handle missing values, inconsistencies, duplicates, and data quality issues.
- ✅ Standardize data types and enforce business rules to handle invalid values, including future birth dates and negative prices.
- 🏗️ Design a well-structured Star Schema with surrogate keys and appropriate relationships.
- 📈 Centralize business logic using dynamic DAX measures for flexible and interactive analysis.
- 📂 Organize measures in a dedicated table to improve model maintainability and usability.

---

🔄 Transformation (Power Query - M)

1️⃣ Staging & Transformation Layers

- Organized queries into Staging and Output layers.
- Preserved raw source data in the staging layer while applying cleaning and transformation logic in the output layer.
- Used Reference instead of Duplicate to reduce redundant transformation logic.

2️⃣ Customer Consolidation

- Combined multiple customer sources into a unified "dim_customers" table.
- Cleaned key columns and removed duplicates to improve data consistency.

3️⃣ Business Rule Enforcement

- 🎂 Handled future dates in "birthdate" by converting invalid values to "null".
- 💰 Corrected negative values in "fact_sales[price]" according to the project's business rules.
- 🔧 Replaced missing prices with "0" where appropriate.
- 📅 Converted integer date columns ("order_date", "ship_date", and "due_date") to the Date data type.
- 🛡️ Applied length-based validation ("Text.Length > 6") to pervent date conversion errors.

4️⃣ Data Standardization & Cleaning

- 👤 Gender: Standardized "M", "F", and null values to "Male", "Female", and "Unknown".
- 💍 Marital Status: Standardized "S", "M", and null values to "Single", "Married", and "Unknown".
- 🚴 Product Line: Standardized "R", "M", "S", and "T" to "Road", "Mountain", "Other Sales", and "Touring".
- 🌍 Consolidated the "country" column.
- 🧼 Applied "Trim" and "Clean" transformations to text columns.

5️⃣ Key Derivation

- Extracted "subcategory_key" and "product_key" from "prd_key".
- Removed leading hyphens and replaced "-" with "_" to standardize key formats and support relationships with subcategory and product dimensions.

---

🏗️ Modeling & DAX

1️⃣ Data Integrity

- Used Left Outer Joins when combining dimension attributes with the fact table.
- Preserved fact records and avoided unintended row loss during data preparation.

2️⃣ Dynamic Sales Calculations

- Removed the pre-calculated sales column to reduce model size.
- Created dynamic measures using "SUMX" to calculate sales from transaction-level data.

3️⃣ Model Standardization

- Applied "snake_case" naming conventions to columns.
- Created surrogate keys for dimension tables to support consistent modeling and reliable relationships.
- Linking the tables by integer columns instead of text columns for the modeling performance.
- Delete source IDs and KEYs after merging tables to reduce the model size, and create surrogarte keys for modeling.

4️⃣ Dynamic Date Dimension

- 📅 Built "dim_date" dynamically using:
  
  "CALENDAR(MIN(order_date), MAX(order_date))"

- Ensured the date dimension covers the date range available in the sales data.

5️⃣ Centralized Measures

- 📊 Created a dedicated measures table to organize key business KPIs, including:

6️⃣ Dynamic Customer Segmentation

- 🧑‍🤝‍🧑 Calculated customer age using "DATEDIFF()".
- Grouped customers into five age categories.
- Created a custom sort column to ensure the correct category order in visualizations.

---

•🆕New abbed column using Power Query (M).
- Customer key
- Product key
- Full_name column was composed from first and last name columns.

🛠️ Tools & Technologies

- 📊 Power BI Desktop — Data Modeling
- 🔄 Power Query (M) — Data Cleaning & Transformation
- 📐 DAX — Dynamic Measures & Business Logic
- ⭐ Star Schema — Dimensional Data Modeling

