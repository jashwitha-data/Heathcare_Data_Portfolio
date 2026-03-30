
---

# 🔷 📁 MINI PROJECT 3

## 📌 Title  
**Qlik Sense Performance Optimization Using SQL Filtering & Data Reduction**

---
# 🔷 Qlik Sense Performance Optimization

## 📌 Overview
This project focuses on improving Qlik Sense performance by reducing data load, optimizing SQL queries, and minimizing RAM usage.

---

## ❗ Problem Statement
Large datasets caused:
- High RAM consumption
- Slow reload times
- Poor dashboard performance

---

## 🧠 Solution Approach
- Applied filters at SQL level
- Converted timestamps in SQL
- Used EXISTS logic to reduce data volume
- Loaded only required columns

---

## 🛠️ Implementation

### SQL Optimization
```sql
WHERE FACILITY_ID IN (...)
AND CAST(CREATE_DATE AT TIME ZONE 'US Mountain Standard Time'
AT TIME ZONE 'India Standard Time' AS DATE)
BETWEEN $(vStartDate) AND $(vEndDate)
```


---

## ✅ Outcome
Reduced data volume significantly
Improved reload speed
Lower RAM usage

---

## 🧰 Tech Stack
Qlik Sense
SQL Server

---

## 🚀 Key Learning

Pushing transformations to SQL significantly improves Qlik performance.
