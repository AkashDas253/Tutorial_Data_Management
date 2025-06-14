## **Year-to-Date (YTD) Facts**

---

### **1. What are Year-to-Date (YTD) Facts?**

**YTD facts** represent **cumulative measures** calculated from the beginning of the calendar (or fiscal) year up to a specified date. They summarize the total or aggregated value of a metric over the year so far.

---

### **2. Purpose of YTD Facts**

* Track **progress** toward annual goals.
* Provide **running totals** for key metrics.
* Help compare current performance against previous years or targets.
* Commonly used in financial, sales, and operational reporting.

---

### **3. Characteristics**

| Attribute           | Description                                                               |
| ------------------- | ------------------------------------------------------------------------- |
| **Cumulative**      | Adds metric values from the start of the year to current date             |
| **Time-Dependent**  | Always calculated relative to a specific date or period                   |
| **Derived Measure** | Often calculated from daily or transactional facts during querying or ETL |

---

### **4. How YTD Facts are Implemented**

| Method                        | Description                                                                                                       |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Calculated at Query Time**  | Aggregate daily or transactional facts up to the selected date (preferred for flexibility)                        |
| **Precomputed in Fact Table** | Store running totals as separate columns or tables (can improve performance but increases storage and complexity) |

---

### **5. Example Use Cases**

| Domain  | Metric              | YTD Example                                   |
| ------- | ------------------- | --------------------------------------------- |
| Sales   | Total Sales Amount  | Sum of all sales from Jan 1 to current date   |
| Finance | Cumulative Expenses | Total expenses incurred year-to-date          |
| HR      | YTD Employee Hours  | Total hours worked by an employee in the year |

---

### **6. Important Notes**

* YTD calculations must consider **calendar or fiscal year boundaries**.
* Time dimension tables should support YTD queries via **date hierarchies**.
* Often combined with **period-to-date (PTD)** or **month-to-date (MTD)** measures.
* Careful with **time zone** or **date format** consistency for accurate YTD calculation.

---

### **7. Example SQL Snippet (Query Time YTD Calculation)**

```sql
SELECT
    Date,
    SUM(Sales_Amount) OVER (
        ORDER BY Date
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS YTD_Sales
FROM Sales_Fact
WHERE Date BETWEEN '2025-01-01' AND CURRENT_DATE;
```

---
