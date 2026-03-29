---

# 🔷 📁 MINI PROJECT 2

## 📌 Title  
**Canonical Master Calendar Implementation in Qlik Sense**

---

## 📄 README.md

```md
# 🔷 Canonical Master Calendar in Qlik Sense

## 📌 Overview
This project demonstrates how to implement a canonical calendar to enable unified date filtering across multiple fact tables.

---

## ❗ Problem Statement
Multiple fact tables had different date fields, making it difficult to apply a single date filter across the dashboard.

---

## 🧠 Solution Approach
- Created a unified date field: `IST_Date`
- Extracted dates from multiple fact tables
- Built a central Master Calendar table

---

## 🛠️ Implementation

```qlik
ALLDates:
Load Distinct IST_Date Resident QUERY_ALERT_RESULTS;

Concatenate (ALLDates)
Load Distinct IST_Date Resident CDI_QRY_ALERTS;

Master_Calendar:
Load
    IST_Date,
    Year(IST_Date) as Year,
    Month(IST_Date) as Month,
    MonthName(IST_Date) as MonthYear,
    Week(IST_Date) as Week,
    Day(IST_Date) as Day
Resident ALLDates;

Drop Table ALLDates;
```qlik

