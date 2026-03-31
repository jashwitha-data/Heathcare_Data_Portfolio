## 🔧 Challenges & Solutions

### 🔹 1. Applying Consistent Filters Across Multiple Tables

#### 📌 Problem

The requirement was to filter the **Query Alerts table** to retrieve only **1 month of data** for specific facilities.

However, additional related tables also needed to reflect the same filtered dataset, even though they were not directly filtered initially. This created a challenge in maintaining **data consistency across multiple fact tables**.

---

#### ⚠️ Root Cause

* Filters were applied only to the primary table (Query Alerts)
* Secondary tables contained larger datasets without restrictions
* Data mismatch occurred when combining tables
* Lack of synchronized filtering logic across tables

---

#### ⚙️ Solution Approach

To ensure consistency across all datasets:

* Applied **SQL-level filtering** on the Query Alerts table to:

  * Restrict data to **1 month**
  * Include only **specific facilities**

* Identified the **common key (ID)** shared across tables

* Used this key to:

  * Filter related records in secondary tables
  * Ensure only relevant data linked to Query Alerts was loaded

* Ensured all tables reflected:

  * Same facility-level filtering
  * Same time-period constraints

---

#### 🧪 Implementation (Conceptual)

```sql
-- Filter primary table (Query Alerts)
WHERE alert_date >= DATEADD(MONTH, -1, GETDATE())
AND facility_id IN ('Facility_A', 'Facility_B')
```

* Secondary tables were filtered using **matching IDs** derived from the primary dataset

---

#### 📈 Outcome

* Achieved **consistent filtering across all related tables**
* Eliminated data mismatches during analysis
* Improved **data relevance and dashboard accuracy**
* Reduced unnecessary data load, improving performance

---

#### 💡 Key Learning

Filtering only the primary dataset is not sufficient in multi-table models.
Ensuring **relational consistency using shared keys** is critical for accurate analytics and reporting.
