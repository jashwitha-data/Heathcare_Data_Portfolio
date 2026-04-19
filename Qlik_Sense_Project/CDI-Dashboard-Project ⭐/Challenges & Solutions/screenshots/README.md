## 📷 Screenshots & Explanation

### 📊 Dashboard Overview

![Dashboard](screenshots/dashboard_overview.png)

This dashboard provides a comprehensive view of CDI tool performance, including:

* Query generation and processing metrics
* Acceptance, rejection, and auto-closure rates
* Revenue impact analysis
* Facility-level performance comparison

---

### 📈 Performance & Facility Analysis

![Performance](screenshots/performance_analysis.png)

This section highlights:

* Facility-wise query distribution
* Accepted vs generated queries
* Revenue contribution per facility
* Identification of high and low performing facilities

---

### 📉 Trend & Query Impact Analysis

![Trends](screenshots/trend_analysis.png)

Key insights include:

* Query accuracy trends over time
* Expected revenue vs system-generated queries
* Top queries contributing to revenue impact
* Identification of critical diagnosis categories

---

### 🧠 Business Insights & Alerts

![Insights](screenshots/business_insights.png)

This section provides actionable insights:

* Accuracy trends and decline reasons
* SLA breaches and processing delays
* Revenue growth opportunities
* Automation efficiency improvements

---

### 🧱 Data Model

![Data Model](screenshots/data_model.png)

The data model includes:

* Multiple fact tables connected via a **Link Table**
* A **Master Calendar** for consistent date filtering
* Facility and query-level relationships
* Optimized structure to avoid synthetic keys

---

## 📈 Final Outcome

* Built an end-to-end **CDI performance monitoring dashboard**
* Enabled **real-time tracking of query lifecycle**
* Improved visibility into **revenue impact and operational efficiency**
* Provided **actionable insights for decision-making**
* Optimized data processing using SQL-level filtering and efficient data modeling

---

## 🚀 Key Takeaways

* Importance of **timezone standardization** in multi-source systems
* Efficient handling of **multi-table filtering using common keys**
* Use of **Master Calendar for consistent date filtering**
* Resolving synthetic keys using **Link Table modeling**
* Performance optimization by shifting transformations to **SQL layer**
