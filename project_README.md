# Customer Behavior & Strategic Growth Analysis
This project presents a comprehensive, end-to-end data analytics pipeline designed to transform raw retail data into high-impact business intelligence. By integrating Python, SQL, and Power BI, the project covers the full lifecycle of data—from rigorous cleaning and structural engineering to complex analytical modeling and executive visualization.

<img width="1920" height="1200" alt="Screenshot (573)" src="https://github.com/user-attachments/assets/75de2591-df02-4b43-9736-d9046c413839" />
<img width="1920" height="1200" alt="Screenshot (572)" src="https://github.com/user-attachments/assets/d2333b67-96eb-4156-a87a-69ba45fec9a5" />


## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Data Architecture & Sources](#2-data-architecture--sources)
3. [Data Cleaning & Preprocessing (Python)](#3-data-cleaning--preprocessing-python)
   - [Null Value Identification](#null-value-identification)
   - [Advanced Imputation Logic](#advanced-imputation-logic)
4. [Structured Data Analysis (SQL)](#4-structured-data-analysis-sql)
5. [Business Intelligence Dashboard (Power BI)](#5-business-intelligence-dashboard-power-bi)
6. [Key Findings & Strategic Insights](#6-key-findings--strategic-insights)
7. [Technical Stack](#7-technical-stack)
8. [How to Run the Project](#8-how-to-run-the-project)

---

## 1. Project Overview
This project delivers an end-to-end data analytics solution, transforming raw transactional records into actionable business intelligence. By leveraging a trifecta of **Python**, **SQL**, and **Power BI**, the analysis uncovers deep-seated patterns in consumer behavior, identifies revenue leakage, and suggests data-backed growth strategies.

## 2. Data Architecture & Sources
The core dataset is a high-granularity transactional log containing over 5,000 entries.
- **Transactional Entities:** Item Name, Category, Purchase Amount, Payment Method, Shipping Type.
- **Customer Profiles:** Age, Gender, Location, Subscription Status (Loyalty).
- **Sentiment Metrics:** Review Ratings (1-5 Scale).

## 3. Data Cleaning & Preprocessing (Python)
The heavy lifting of data integrity was performed using the **Pandas** and **NumPy** libraries in a Jupyter Notebook environment.

### Null Value Identification
We utilized `df.info()` and `df.isnull().sum()` to pinpoint missing data clusters:
- **Review Rating:** 601 nulls.
- **Purchase Amount:** 556 nulls.
- **Size/Color:** ~300-400 nulls each.

### Advanced Imputation Logic
To prevent statistical bias, we avoided simple mean-fills:
- **Amount & Rating:** Imputed using **Category-wise Median** to preserve the unique price points of Electronics vs. Clothing.
- **Subscription Status:** Nulls were logically mapped to 'No' (Standard User), assuming a lack of record implies a lack of enrollment.
- **Size:** Imputed with the **Mode** of the specific Item Type.

## 4. Structured Data Analysis (SQL)
SQL was employed to simulate enterprise-level data retrieval:
- **Window Functions:** `RANK()` and `DENSE_RANK()` used to find the top 3 items by revenue per category.
- **Aggregations:** Calculating Average Order Value (AOV) by Payment Method.
- **Filtering:** isolating high-value customer cohorts (Age > 50 with Spend > $200).

## 5. Business Intelligence Dashboard (Power BI)
The Power BI layer serves as the stakeholder interface, featuring:
- **DAX Calculations:** Custom measures for 'Subscription Conversion Rate' and 'Total Revenue Growth'.
- **Dynamic Filtering:** Slicers for Category, Subscription and Gender to allow for granular exploration.
- **Visual Insights:** Decomposition trees to see what factors most influence high review ratings.

## 6. Key Findings & Strategic Insights
- **The Loyalty Premium:** Subscribed customers spend **~60% more** ($235.62 avg) compared to non-subscribers ($146.75 avg).
- **Seasonal Sensitivity:** Peak revenue occurs in **Spring/Summer**, suggesting a 20% budget increase for marketing during Q2.
- **Category Performance:** **Electronics** accounts for 55% of revenue but has the lowest average rating (2.9/5), indicating a need for quality control or post-purchase support improvements.

## 7. Technical Stack
- **Languages:** Python (Pandas, NumPy, Seaborn, Matplotlib, Plotly, Sqlalchemy), SQL (PostgreSQL/MySQL).
- **Tools:** Power BI Desktop, Google Colab, Excel, SQL Workbench, Ngrok.
- **Environment:** Excel (Initial Audit).

## 8. Report
- **Insights:** A report in pdf format is given to understand about data and project better. Key insights has also been presented.

## 8. How to Run the Project
1. **Prepare Data:** Place the `customer_shopping_behavior.csv` in the root directory.
2. **Clean:** Run the `Customer_behaviour_analysis_data_cleaning_eda.ipynb` to generate `cust_behav_cleaned_data.csv`.
3. **Query:** Use the `Customer_behavior_business_insights_sql.sql` to create views and perform cohort analysis.
4. **Visualize:** Open `Cust_behav.pbix` and refresh the data source to view updated charts.
