## **Data Validation Testing**

---

### **Overview**

**Data Validation Testing** is a core part of ETL Testing focused on ensuring that **data extracted from source systems** is **accurately and completely loaded** into the target system (e.g., data warehouse) without **loss, duplication, or corruption**.

---

### **Objectives of Data Validation Testing**

* Confirm **data consistency** between source and target
* Ensure **data completeness** (no missing/truncated values)
* Validate **column-level** and **row-level** accuracy
* Check for **unexpected nulls**, incorrect formats, or invalid values
* Maintain **referential integrity** and **business rules compliance**

---

### **1. Key Types of Data Validation Tests**

| Type                          | Description                                                           |
| ----------------------------- | --------------------------------------------------------------------- |
| **Row Count Validation**      | Ensure the number of records in source = target                       |
| **Column-Level Validation**   | Ensure each column's values match between source and target           |
| **Duplicate Check**           | Verify no unintended duplicates are present in target                 |
| **Null/Default Checks**       | Ensure fields required by schema are not null or improperly defaulted |
| **Data Format Validation**    | Validate format constraints (e.g., date, currency, phone, email)      |
| **Data Type Validation**      | Ensure data types match expected target schema                        |
| **Boundary Testing**          | Ensure numeric/string values are within valid range                   |
| **Reference Data Validation** | Ensure FK values exist in parent tables (e.g., product\_id exists)    |
| **Business Rule Validation**  | Ensure business logic/derived values are computed correctly           |

---

### **2. Sample Data Validation Test Cases**

| Test Case ID | Scenario                   | Source Table | Target Table   | Validation Logic                    |
| ------------ | -------------------------- | ------------ | -------------- | ----------------------------------- |
| TC\_VAL\_001 | Row count match            | customers    | dim\_customers | COUNT(source) = COUNT(target)       |
| TC\_VAL\_002 | City column data match     | orders       | fact\_orders   | orders.city = fact\_orders.city     |
| TC\_VAL\_003 | Null check on customer\_id | orders       | fact\_orders   | customer\_id IS NOT NULL            |
| TC\_VAL\_004 | Date format validation     | transactions | fact\_txn      | txn\_date LIKE 'YYYY-MM-DD'         |
| TC\_VAL\_005 | Derived field validation   | orders       | fact\_orders   | total\_amt = quantity × unit\_price |

---

### **3. Tools & Techniques for Validation**

| Tool/Method                | Usage                                     |
| -------------------------- | ----------------------------------------- |
| **SQL Queries**            | Manual validation of source vs target     |
| **ETL Testing Tools**      | QuerySurge, Informatica DVO, Talend       |
| **Excel/CSV Comparison**   | For small data sets                       |
| **Python/Pandas Scripts**  | Automated row-wise and column-wise checks |
| **Reconciliation Reports** | Generate pass/fail summaries              |

---

### **4. Best Practices**

* Use **sample test data** before production runs
* Compare **specific columns** (not SELECT \*)
* Validate **after every ETL phase** (not just final load)
* Handle **data type casting** carefully during SQL comparisons
* **Log mismatches** with row numbers and details for debugging
* Test **both positive and negative scenarios**

---

### **5. Challenges in Data Validation Testing**

| Challenge                     | Description                                            |
| ----------------------------- | ------------------------------------------------------ |
| **Large Volumes**             | Validating millions of rows is time-consuming          |
| **Complex Joins**             | Data spread across multiple normalized tables          |
| **Transformation Logic**      | Must replicate logic to validate derived fields        |
| **Source System Changes**     | Schema or logic changes in source can break validation |
| **Floating Point Mismatches** | Minor rounding differences cause false mismatches      |

---

### **6. Sample SQL Snippets**

**Row Count Check**

```sql
SELECT COUNT(*) FROM source_table;
SELECT COUNT(*) FROM target_table;
```

**Column Data Match**

```sql
SELECT source.col, target.col
FROM source_table source
JOIN target_table target ON source.id = target.id
WHERE source.col <> target.col;
```

**Null Check**

```sql
SELECT * FROM target_table WHERE important_column IS NULL;
```

---
