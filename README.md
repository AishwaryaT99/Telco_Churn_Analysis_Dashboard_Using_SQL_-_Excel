#  Customer Churn Analysis Dashboard (SQL + Excel)

##  Project Overview

This project analyzes customer churn data from a telecom company to identify patterns and factors that contribute to customer attrition.
The analysis was performed using **MySQL** for data querying and **Microsoft Excel** for data visualization and dashboard creation.

The dashboard provides interactive insights into customer churn using **Pivot Tables, Charts, and Slicers**.

---

##  Project Objectives

* Analyze customer churn trends
* Identify high-risk customer segments
* Understand the impact of contract type, tenure, and charges on churn
* Build an interactive Excel dashboard for business insights

---

##  Tools & Technologies

* SQL (MySQL Workbench)
* Microsoft Excel
* Pivot Tables
* Pivot Charts
* Slicers
* Data Cleaning & Aggregation

---

##  Dataset

Dataset used: **Telco Customer Churn Dataset**

Source: Kaggle
https://www.kaggle.com/datasets/blastchar/telco-customer-churn

The dataset contains **7043 customer records** and **21 columns**, including:

* Customer demographics
* Service subscriptions
* Billing details
* Churn status

---

##  SQL Analysis Queries

### Overall Churn Rate

```sql
SELECT 
COUNT(*) AS total_customers,
SUM(CASE WHEN churn='Yes' THEN 1 ELSE 0 END) AS churned_customers,
ROUND(SUM(CASE WHEN churn='Yes' THEN 1 ELSE 0 END)*100/COUNT(*),2) AS churn_rate
FROM customers;
```

### Churn by Contract Type

```sql
SELECT contract,
COUNT(*) AS total_customers,
SUM(CASE WHEN churn='Yes' THEN 1 ELSE 0 END) AS churned
FROM customers
GROUP BY contract;
```

### Churn by Tenure Group

```sql
SELECT 
CASE 
WHEN tenure <=6 THEN '0-6 Months'
WHEN tenure <=12 THEN '6-12 Months'
WHEN tenure <=24 THEN '1-2 Years'
ELSE '2+ Years'
END AS tenure_group,
COUNT(*) AS total_customers,
SUM(CASE WHEN churn='Yes' THEN 1 ELSE 0 END) AS churned
FROM customers
GROUP BY tenure_group;
```

### Average Monthly Charges

```sql
SELECT churn,
ROUND(AVG(monthlycharges),2) AS avg_monthly_charges
FROM customers
GROUP BY churn;
```

---

##  Excel Dashboard

An interactive dashboard was created in Excel using:

* Pivot Tables
* Pivot Charts
* KPI Cards
* Slicers for filtering

### Dashboard Features

* Total Customers KPI
* Churn Rate KPI
* Churn by Contract Type
* Churn by Tenure Group
* Churn by Internet Service
* Interactive slicers for filtering data

### Slicers Used

* Gender
* Contract
* Internet Service
* Payment Method
* Tenure Group

These slicers allow users to dynamically filter the dashboard and analyze churn patterns.

---

##  Key Insights

* Customers with **Month-to-Month contracts have the highest churn rate**
* **New customers (0–6 months tenure)** churn more frequently
* Customers with **higher monthly charges** tend to churn more
* Long-term contracts significantly reduce churn risk

---

##  Dashboard Preview

<img width="689" height="392" alt="image" src="https://github.com/user-attachments/assets/6470620e-0790-413e-8f52-8209e24f0051" />

---

##  Business Recommendations

* Offer incentives for long-term contracts
* Provide onboarding support for new customers
* Introduce loyalty rewards for high-value customers
* Optimize pricing plans to reduce churn

---

##  Future Improvements

* Build the dashboard in Power BI
* Create predictive churn model using Python
* Automate data refresh using Power Query

---

##  Author

Aishwarya Tippannawar

Aspiring Data Analyst | SQL | Excel | Data Visualization






