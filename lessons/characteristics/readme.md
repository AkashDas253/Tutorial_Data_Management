## 📘 Data Warehousing: Characteristics 

---

### 🔍 Overview

A data warehouse has **four fundamental characteristics** that distinguish it from other database systems. These were defined by **Bill Inmon**, known as the "father of data warehousing." They help ensure that the warehouse is suitable for **decision support**, **analytical querying**, and **business intelligence.**

---

### ✅ 1. **Subject-Oriented**

| Feature | Description |
|--------|-------------|
| **Definition** | Organized around key business subjects like sales, customers, products, etc., rather than processes or applications. |
| **Purpose** | Focuses on analyzing specific subjects instead of general operations. |
| **Effect** | Allows meaningful data grouping for decision-making. |

> *E.g., A subject like “Sales” would include all customer purchases, regions, products, and revenue.*

---

### 🔁 2. **Integrated**

| Feature | Description |
|--------|-------------|
| **Definition** | Combines data from various heterogeneous sources into a consistent format. |
| **Purpose** | Eliminates inconsistencies in naming, coding, and measurement units. |
| **Effect** | Ensures data quality and uniformity across the warehouse. |

> *E.g., Combining "Customer_ID" from CRM with "Cust_ID" from billing into a unified format.*

---

### 📅 3. **Time-Variant**

| Feature | Description |
|--------|-------------|
| **Definition** | Stores historical data snapshots along with current data. |
| **Purpose** | Tracks trends, patterns, and changes over time. |
| **Effect** | Supports longitudinal studies and forecasting. |

> *E.g., A sales data table may retain daily records over 5 years to support trend analysis.*

- **Time-stamped**: All records include a time dimension (e.g., Date, Quarter).
- **No Update/Delete**: Old data is retained for reference, not overwritten.

---

### 🛑 4. **Non-Volatile**

| Feature | Description |
|--------|-------------|
| **Definition** | Once data enters the warehouse, it is not modified or deleted by end users. |
| **Purpose** | Maintains data consistency and accuracy for reporting. |
| **Effect** | Ensures historical data remains intact for future audits or analysis. |

> *E.g., Once February’s sales are loaded, they are not changed—even if the sales system corrects a mistake later.*

---

### 📌 Summary Table

| Characteristic    | Focus                         | Benefit |
|------------------|-------------------------------|---------|
| Subject-Oriented | Organizes by business themes  | Better analytical clarity |
| Integrated       | Merges inconsistent sources    | Uniform, clean data |
| Time-Variant     | Historical + current data      | Trend analysis & forecasting |
| Non-Volatile     | Data is stable post-load       | Reliable & auditable data |

---
