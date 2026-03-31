# 🔷 Qlik Sense Portfolio

## 👨‍💻 About Me
Aspiring Data Analyst skilled in Qlik Sense, SQL, and Data Modeling.

---
# 🔷 Qlik Sense Portfolio

## 📊 Projects

### ⭐ CDI Tool Performance Dashboard
## 🔹 📌 Project Overview
This project focuses on building a **high-performance Qlik Sense dashboard** to analyze CDI (Clinical Documentation Improvement) tool performance across multiple facilities.

The solution integrates **multiple fact tables**, applies **complex filtering**, and ensures **accurate time-based analysis** using a unified calendar model.

---

## 🔷 🏗️ Architecture Overview
- **Data Source:** Microsoft SQL Server  
- **Data Processing:** SQL + Qlik Load Script  
- **Data Model:** Multi-Fact Model with Master Calendar  
- **Visualization:** Qlik Sense Dashboard  

---

## 🔷 🧩 Data Model Design

### ✔ Fact Tables
- `QUERY_ALERT_RESULTS` → Query-level data  
- `PAT_VISIT` → Patient visit details  
- `PAT_CODING_INFO` → Financial & coding data  
- `CDI_QRY_ALERTS` → CDI alerts tracking  

### ✔ Key Design Approach
- Used `PAT_ENC_ID` as a common linking key  
- Avoided synthetic keys using controlled joins and `EXISTS` logic  
- Implemented **Master Calendar** using a common date field (`IST_Date`)  

---

## 🔷 🗓️ Master Calendar Implementation

```qlik 
ALLDates:
Load Distinct IST_Date Resident [QUERY_ALERT_RESULTS];

Concatenate (ALLDates)
Load Distinct IST_Date Resident [CDI_QRY_ALERTS];

Master_Calendar:
Load
    Distinct IST_Date,
    Year(IST_Date) as Year,
    Month(IST_Date) as Month,
    MonthName(IST_Date) as MonthYear,
    Week(IST_Date) as Week,
    Day(IST_Date) as Day
Resident ALLDates;
Drop Table ALLDates;
```

✔ Enables unified filtering across multiple fact tables

---

## 🔷 🔄 Key Transformations

### ✔ Timestamp Conversion (SQL Layer)
- Converted timestamps from:
  - **US Mountain Time → India Standard Time**
- Ensed consistency across all fact tables  

```sql
CAST(CREATE_DATE AT TIME ZONE 'US Mountain Standard Time'
AT TIME ZONE 'India Standard Time' AS DATE) AS IST_Date
```

### ✔ Data Filtering Optimization
- Applied filters in SQL:
  - Facility-based filtering  
  - Date range filtering using variables (`vStartDate`, `vEndDate`)  
- Used `EXISTS` clause to reduce data volume  

---

## 🔷 ⚡ Performance Optimization Techniques
- Applied SQL-level filtering to reduce data load  
- Used `EXISTS` logic to limit unnecessary joins  
- Selected only required columns  
- Implemented date range variables (`vStartDate`, `vEndDate`)  
- Reduced RAM usage during reload

---

## 🔷 🚧 Challenges & Solutions

### 🔹 1. Multiple Filters Across Fact Tables
- **Challenge:** Applying filters consistently across multiple datasets  
- **Solution:** Standardized keys and applied SQL-level filtering  

### 🔹 2. Timestamp Conversion
- **Challenge:** Different time zones causing inconsistent reporting  
- **Solution:** Centralized conversion in SQL layer  

### 🔹 3. Multiple Fact Tables with Master Calendar
- **Challenge:** Linking multiple fact tables with a single calendar  
- **Solution:** Created a unified calendar using common date field  

### 🔹 4. Synthetic Keys Issue
- **Challenge:** Auto-generated synthetic keys due to multiple associations  
- **Solution:** Used `EXISTS` and controlled joins to avoid ambiguity  

### 🔹 5. High Memory Usage
- **Challenge:** Large data causing high RAM consumption  
- **Solution:** Pre-filtered data in SQL and optimized load script  

---

## 🔷 📈 Dashboard Features

### ✔ KPI Cards
- Total Queries  
- Dropped Queries  
- Accuracy %  
- Avg Processing Time  
- Revenue Impact  

### ✔ Visualizations
- Query Accuracy Trend  
- Facility-wise Performance  
- Top Queries by Impact  
- Time-based performance trends  

### ✔ Interactive Filters
- Date  
- Facility  
- Facility Type  

---

## 🔷 📸 Dashboard Screenshots

> Upload your images into an `/images` folder in the repository.

---

## 🔷 🛠️ Tech Stack
- Qlik Sense  
- SQL Server  
- Data Modeling (Multi-Fact, Master Calendar)  
- Set Analysis  
- Performance Optimization  

---

## 🔷 🚀 Key Outcomes
- Improved dashboard performance  
- Reduced data load time and memory usage  
- Enabled accurate multi-fact analysis  
- Delivered scalable and maintainable data model  

