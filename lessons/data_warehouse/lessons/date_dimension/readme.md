## **Date Dimension**

---

### **1. What is a Date Dimension?**

A **Date Dimension** is a **specialized dimension table** that stores **date-related attributes** to provide context and enable time-based analysis in a data warehouse.

---

### **2. Purpose**

* Support time-based slicing, dicing, and filtering of facts
* Enable easy querying by date parts (year, month, quarter, day, etc.)
* Facilitate time series analysis, trend reporting, and period comparisons

---

### **3. Key Characteristics**

| Attribute                                                    | Description |
| ------------------------------------------------------------ | ----------- |
| Covers a **range of dates** (e.g., many years)               |             |
| Contains **granular date details** (day-level usually)       |             |
| Has multiple **date parts** as attributes                    |             |
| Supports **hierarchies** for drill-down (Year → Month → Day) |             |
| Usually has a **surrogate key** as primary key               |             |

---

### **4. Common Columns / Attributes**

| Column Name        | Description                                     |
| ------------------ | ----------------------------------------------- |
| **Date\_Key**      | Surrogate key (usually integer YYYYMMDD format) |
| **Full\_Date**     | Actual date value                               |
| **Year**           | Calendar year                                   |
| **Quarter**        | Quarter of the year (1 to 4)                    |
| **Month**          | Month number (1 to 12)                          |
| **Month\_Name**    | Month name (January, February, etc.)            |
| **Day**            | Day of the month (1 to 31)                      |
| **Day\_of\_Week**  | Day number in the week (1 to 7)                 |
| **Day\_Name**      | Name of the day (Monday, Tuesday, etc.)         |
| **Week\_of\_Year** | Week number of the year                         |
| **Is\_Weekend**    | Boolean or flag indicating weekend or weekday   |
| **Fiscal\_Year**   | Fiscal year (if different from calendar year)   |
| **Holiday\_Flag**  | Indicates whether the date is a holiday         |

---

### **5. Additional Optional Attributes**

* **Is\_Month\_Start**, **Is\_Month\_End** flags
* **Is\_Quarter\_Start**, **Is\_Quarter\_End** flags
* **Is\_Year\_Start**, **Is\_Year\_End** flags
* **Fiscal\_Quarter**, **Fiscal\_Month**
* **Previous\_Date\_Key** for easier navigation

---

### **6. Benefits of Using Date Dimension**

* Avoids complex date calculations in queries
* Improves query performance by precomputing date attributes
* Simplifies report generation and analytics
* Supports business-specific calendars (fiscal, academic)

---

### **7. Design Considerations**

* Populate date dimension for a **wide date range** (past and future)
* Use a **surrogate key** (usually integer) for joins to fact tables
* Handle **different calendar systems** if needed (e.g., fiscal calendar)
* Keep it **static** (non-volatile) once populated

---

### **8. Example Schema**

| Date\_Key | Full\_Date | Year | Quarter | Month | Month\_Name | Day | Day\_of\_Week | Day\_Name | Week\_of\_Year | Is\_Weekend | Fiscal\_Year | Holiday\_Flag |
| --------- | ---------- | ---- | ------- | ----- | ----------- | --- | ------------- | --------- | -------------- | ----------- | ------------ | ------------- |
| 20250607  | 2025-06-07 | 2025 | 2       | 6     | June        | 7   | 6             | Saturday  | 23             | Yes         | 2025         | No            |

---

### **9. Usage in Queries**

* Filtering facts by year, quarter, month
* Comparing performance year-over-year or month-over-month
* Rolling up data by week, month, quarter, year
* Identifying weekends and holidays in reports

---
