### 🔹 4. Handling Synthetic Keys using Link Table Modeling

#### 📌 Problem

The data model involved **two fact tables** that required multiple common fields (filters) such as IDs and date fields to be associated between them.

When these tables were loaded into Qlik, it resulted in the creation of **synthetic keys**, leading to:

* Data model complexity
* Ambiguous relationships
* Incorrect aggregations in dashboards

---

#### ⚠️ Root Cause

* Multiple common fields existed between the same fact tables
* Qlik automatically created **synthetic keys** due to these overlapping fields
* Lack of a proper data model structure to manage relationships
* Direct connections between fact tables caused ambiguity

---

#### ⚙️ Solution Approach

To resolve synthetic keys and create a scalable data model:

* Identified all **common fields** shared between the fact tables (e.g., ID, Date, Facility)

* Created a **Link Table** that:

  * Contained unique combinations of these common fields
  * Acted as a bridge between both fact tables

* Removed direct associations between fact tables

* Connected both fact tables **only through the Link Table**

* Ensured all filters (dimensions) were applied via the Link Table

---

#### 🧪 Implementation (Conceptual - Qlik)

```qlik id="p4x8kd"
LinkTable:
LOAD DISTINCT
    Common_ID,
    Date,
    Facility
RESIDENT FactTable1;

CONCATENATE (LinkTable)
LOAD DISTINCT
    Common_ID,
    Date,
    Facility
RESIDENT FactTable2;
```

* Dropped duplicate key fields from fact tables after linking
* Maintained a clean **star-schema-like structure**

---

#### 📈 Outcome

* Eliminated synthetic keys
* Simplified and optimized data model
* Ensured accurate aggregations and filtering
* Improved dashboard performance and reliability

---

#### 💡 Key Learning

In Qlik, when multiple tables share more than one common field, a **Link Table approach** is essential.
It prevents synthetic keys, ensures clarity in relationships, and creates a scalable data model for complex dashboards.
