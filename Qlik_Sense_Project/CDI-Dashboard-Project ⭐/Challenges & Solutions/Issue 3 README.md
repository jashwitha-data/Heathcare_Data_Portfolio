### 🔹 3. Creating a Master Calendar for Consistent Date Filtering

#### 📌 Problem

The dataset contained multiple records (queries) generated on the same date across different tables.

Directly using these date fields for filtering caused:

* Duplicate date values
* Inconsistent filtering behavior
* Difficulty in applying a single date filter across the dashboard

A **unique and centralized date reference** was required for accurate and consistent filtering.

---

#### ⚠️ Root Cause

* Date fields existed in multiple tables
* Multiple records shared the same date (non-unique values)
* No centralized date dimension to control filtering
* Direct filtering on fact tables led to inconsistent results

---

#### ⚙️ Solution Approach

To resolve this, a **Master Calendar (Date Dimension Table)** was created:

* Generated a **distinct list of dates** covering the required data range

* Created a separate table containing:

  * Unique Date
  * Year
  * Month
  * Day
  * Week

* Linked the Master Calendar to fact tables using the **date field**

* Ensured all dashboard filters used the **Master Calendar date field** instead of individual table dates

---

#### 🧪 Implementation (Conceptual - Qlik)

```qlik id="q7l2nx"
MasterCalendar:
LOAD DISTINCT
    Date(IST_Timestamp) as Date,
    Year(IST_Timestamp) as Year,
    Month(IST_Timestamp) as Month,
    Day(IST_Timestamp) as Day
RESIDENT FactTable;
```

* Used the standardized **IST timestamp** for consistency
* Established relationship between Master Calendar and all relevant tables

---

#### 📈 Outcome

* Enabled **single, consistent date filter** across the dashboard
* Eliminated duplicate date issues
* Improved usability of time-based analysis
* Simplified dashboard design and user interaction

---

#### 💡 Key Learning

Using a **Master Calendar (date dimension)** is essential in dashboards with multiple records per date.
It ensures clean filtering, better performance, and a consistent user experience.
