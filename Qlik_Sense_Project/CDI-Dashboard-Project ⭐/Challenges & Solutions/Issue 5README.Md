### 🔹 5. Optimizing Data Load by Shifting Filters from Qlik to SQL

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

```sql id="z8k3mn"
SELECT *
FROM QueryAlerts
WHERE alert_date >= DATEADD(MONTH, -1, GETDATE())
AND facility_id IN ('Facility_A', 'Facility_B')
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

#### 💡 Key Learning

Applying filters at the **data source level (SQL)** is a best practice for performance optimization.
It ensures efficient data processing and allows BI tools like Qlik to focus on analytics rather than heavy data handling.
