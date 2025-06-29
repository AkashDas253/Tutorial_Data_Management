## **Data Integrity Testing**

---

### **Overview**

**Data Integrity Testing** ensures that data in the data warehouse or ETL process is **accurate, consistent, and reliable** throughout its lifecycle—from source extraction through transformation to loading into the target. It verifies that data remains unchanged, correctly transformed, and conforms to business rules.

---

### **Objectives**

* Validate **accuracy and consistency** of data after ETL
* Ensure **no data loss, duplication, or corruption** during movement
* Confirm **business rules and data constraints** are enforced
* Verify **referential integrity** between related tables
* Detect and resolve **discrepancies between source and target** data

---

### **1. Key Areas in Data Integrity Testing**

| Area                        | Focus                                                              |
| --------------------------- | ------------------------------------------------------------------ |
| Source to Target Validation | Check row counts, sums, and data matches between source and target |
| Transformation Validation   | Verify correctness of data transformations and calculations        |
| Duplicate Records Check     | Identify and handle duplicates properly                            |
| Referential Integrity       | Ensure foreign key relationships are maintained                    |
| Null and Default Values     | Validate mandatory fields and default value assignments            |
| Data Format and Type        | Confirm data types and formats match specifications                |

---

### **2. Sample Test Scenarios**

| Test Case ID | Scenario                                        | Expected Outcome                                |
| ------------ | ----------------------------------------------- | ----------------------------------------------- |
| TC\_DI\_001  | Validate row count between source and target    | Counts should be equal                          |
| TC\_DI\_002  | Verify sum of sales amount after transformation | Aggregated totals should match expected results |
| TC\_DI\_003  | Check for duplicate customer records            | No duplicates found in target                   |
| TC\_DI\_004  | Validate foreign key constraints                | All child keys exist in parent tables           |
| TC\_DI\_005  | Check null values in NOT NULL columns           | No null values present                          |

---

### **3. Tools & Techniques**

| Tool/Method           | Usage                                                    |
| --------------------- | -------------------------------------------------------- |
| SQL Queries           | Validate counts, sums, duplicates, referential integrity |
| ETL Tool Logs         | Review transformation steps and error logs               |
| Data Profiling Tools  | Identify anomalies, duplicates, and data quality issues  |
| Automation Scripts    | Automate validations and comparisons                     |
| BI Reports/Dashboards | Cross-check metrics and KPIs                             |

---

### **4. Sample SQL Queries**

**Compare row counts between source and target**

```sql
SELECT 
  (SELECT COUNT(*) FROM source_table) AS source_count,
  (SELECT COUNT(*) FROM target_table) AS target_count;
```

**Check for duplicates on customer\_id**

```sql
SELECT customer_id, COUNT(*) 
FROM target_table 
GROUP BY customer_id 
HAVING COUNT(*) > 1;
```

**Validate sum of sales\_amount**

```sql
SELECT 
  (SELECT SUM(sales_amount) FROM source_sales) AS source_sum,
  (SELECT SUM(sales_amount) FROM target_sales) AS target_sum;
```

**Check for nulls in NOT NULL column**

```sql
SELECT COUNT(*) 
FROM target_table 
WHERE important_column IS NULL;
```

---

### **5. Best Practices**

* Perform data integrity checks at **each ETL phase** (extract, transform, load)
* Automate key integrity validations for faster feedback
* Maintain consistent test data sets for reproducible results
* Document all data integrity rules and validation criteria
* Integrate integrity tests into regression testing cycles
* Collaborate with business users for validation of business rules

---

### **6. Challenges**

| Challenge                   | Description                                          |
| --------------------------- | ---------------------------------------------------- |
| Complex Transformations     | Difficult to validate derived or aggregated data     |
| Large Data Volumes          | Performance issues in validating big datasets        |
| Data Source Variability     | Inconsistent source data affects integrity           |
| Handling Nulls and Defaults | Differentiating between valid nulls and missing data |

---
