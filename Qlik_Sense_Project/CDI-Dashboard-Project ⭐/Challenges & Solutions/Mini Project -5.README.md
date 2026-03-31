# 🔷 📁 MINI PROJECT 5

## 📌 Title  

## 🔧 Challenges & Solutions : Optimizing Data Load by Shifting Filters from Qlik to SQL

#### 📌 Problem

Initially, data was being fully loaded into Qlik and then filtered within the application layer.

This approach led to:

* Increased data load time
* Higher memory consumption
* Slower dashboard performance

The requirement was to improve efficiency by minimizing the volume of data loaded into Qlik.

---

#### ⚠️ Root Cause

* Filters were applied **after data load** in Qlik
* Large datasets were unnecessarily loaded into memory
* Increased processing overhead within Qlik
* Inefficient use of database capabilities

---

#### ⚙️ Solution Approach

To optimize performance, filtering logic was shifted from Qlik to SQL:

* Applied all major filters directly at the **SQL extraction level**, including:

  * Date range filtering (1 month data)
  * Facility-level filtering
  * Relevant record selection

* Ensured only **required and relevant data** was extracted from the source

* Reduced dependency on Qlik for heavy data transformations

* Used Qlik primarily for:

  * Data modeling
  * Visualization
  * Final transformations

---

#### 🧪 Implementation (Conceptual)

```sql
WHERE FACILITY_ID IN (...)
AND CAST(CREATE_DATE AT TIME ZONE 'US Mountain Standard Time'
AT TIME ZONE 'India Standard Time' AS DATE)
BETWEEN $(vStartDate) AND $(vEndDate)
```

* Similar filtering logic applied across all related tables
* Maintained consistency with business requirements

---

#### 📈 Outcome

* Significantly reduced data load volume
* Improved dashboard performance and responsiveness
* Reduced memory usage in Qlik
* Faster data refresh cycles

---

#### 🔄 Before vs After Improvements

**Before:**
![Before Performance](screenshots/before_performance.png)

* Full data loaded into Qlik
* Slow performance and high memory usage

**After:**
![After Performance](screenshots/after_performance.png)

* Applied filters at SQL level
* Reduced data load volume
* Faster dashboard performance

---
  
#### 💡 Key Learning

Applying filters at the **data source level (SQL)** is a best practice for performance optimization.
It ensures efficient data processing and allows BI tools like Qlik to focus on analytics rather than heavy data handling.
