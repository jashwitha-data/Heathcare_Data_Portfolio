### 🔹 2. Timezone Standardization Across Multiple Fact Tables

#### 📌 Problem

The project involved two fact tables containing timestamp data in different timezones:

* One table in **UTC**
* Another in **US Mountain Standard Time (MST)**

For accurate reporting, both tables needed to be filtered and analyzed using a **common timezone (IST)**.

Without standardization, applying date filters resulted in **inconsistent and incorrect data across tables**.

---

#### ⚠️ Root Cause

* Different source systems stored timestamps in different timezones
* Direct filtering caused **date misalignment** between datasets
* Events from the same time period appeared under different dates
* No unified time reference for reporting

---

#### ⚙️ Solution Approach

To ensure consistency in reporting:

* Standardized both datasets into a **single timezone (IST)**

* Applied timezone conversions:

  * UTC → IST (**+5 hours 30 minutes**)
  * MST → IST (**+12 hours 30 minutes**)

* Performed conversion:

  * Either at **SQL level** during data extraction
  * Or within **Qlik transformation layer**

* Ensured all date filters were applied **only after conversion to IST**

---

#### 🧪 Implementation (Conceptual)

```sql id="x9m2pl"
-- Example: Converting UTC to IST
DATEADD(MINUTE, 330, utc_timestamp)

-- Example: Converting MST to IST
DATEADD(HOUR, 12, mst_timestamp) + DATEADD(MINUTE, 30, mst_timestamp)
```

* Created standardized timestamp fields (e.g., `IST_Timestamp`)
* Used these fields for all filtering and reporting

---

#### 📈 Outcome

* Achieved **uniform time reference across all tables**
* Eliminated discrepancies in date-based reporting
* Enabled accurate filtering for dashboards
* Improved reliability of time-based KPIs

---

#### 💡 Key Learning

In multi-source data systems, **timezone standardization is critical** before applying any filters.
A unified time reference ensures consistency, accuracy, and reliable analytics.
