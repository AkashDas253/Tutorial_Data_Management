## **Data Completeness Testing**

---

### **Overview**

**Data Completeness Testing** is a critical phase in ETL testing that ensures **all expected data is extracted, transformed, and loaded** without loss, truncation, or omission. It validates that **no partial data** or **missing records** exist in the target system.

---

### **Objectives of Data Completeness Testing**

* Ensure **all source data is loaded** into the target
* Verify **no missing records, fields, or values**
* Detect **incomplete rows, columns, or files**
* Confirm **correct handling of nulls, defaults, and optional fields**
* Validate completeness in both **row-level and column-level**

---

### **1. Key Types of Completeness Checks**

| Type                          | Description                                                                |
| ----------------------------- | -------------------------------------------------------------------------- |
| **Row Count Check**           | Compare number of records between source and target                        |
| **Column-Level Completeness** | Ensure no truncation or loss of field values during transformation or load |
| **File-Level Completeness**   | Ensure all expected files are processed and no file is missed/skipped      |
| **Null Checks**               | Confirm mandatory fields are populated, and nulls are handled as expected  |
| **Data Boundary Checks**      | Ensure data values fall within valid and expected ranges                   |
| **Partition Completeness**    | Validate that all date/time partitions are present (e.g., daily loads)     |
| **Delta Load Completeness**   | Ensure all incremental changes are correctly captured and loaded           |

---

### **2. Sample Test Scenarios**

| Test Case ID | Scenario                       | Source         | Target        | Validation Rule                         |
| ------------ | ------------------------------ | -------------- | ------------- | --------------------------------------- |
| TC\_DC\_001  | Validate row count             | customer\_src  | customer\_dim | COUNT(source) = COUNT(target)           |
| TC\_DC\_002  | Check missing columns          | product\_src   | product\_dim  | All columns must be present             |
| TC\_DC\_003  | Null check on mandatory fields | txn\_src       | fact\_txn     | txn\_date IS NOT NULL                   |
| TC\_DC\_004  | File-level check               | inbound\_files | staging\_area | All 10 daily files should be processed  |
| TC\_DC\_005  | Daily load completeness        | sales\_data    | sales\_fact   | 1 row per store per day must exist      |
| TC\_DC\_006  | Verify delta completeness      | order\_log     | fact\_orders  | All updated records in log appear in DW |

---

### **3. Tools & Techniques for Testing**

| Method/Tool               | Usage                                                       |
| ------------------------- | ----------------------------------------------------------- |
| **SQL Queries**           | Row count, null, missing value checks                       |
| **File Comparison Tools** | Validate number and size of files between source and target |
| **ETL Logs**              | Use job logs to verify processed record/file counts         |
| **Python/Pandas Scripts** | Automate missing row/value detection for large datasets     |
| **QuerySurge, Talend DQ** | Automate completeness and quality checks                    |

---

### **4. Sample SQL Snippets**

**Row Count Validation**

```sql
SELECT COUNT(*) FROM source_table;
SELECT COUNT(*) FROM target_table;
```

**Check for Missing Records**

```sql
SELECT id FROM source_table
EXCEPT
SELECT id FROM target_table;
```

**Column Completeness (Null Check)**

```sql
SELECT * FROM target_table WHERE important_column IS NULL;
```

**Partition Completeness (Daily Load)**

```sql
SELECT load_date, COUNT(*) 
FROM target_table 
GROUP BY load_date 
ORDER BY load_date;
```

---

### **5. Best Practices**

* Always compare **source and target record counts**
* Monitor **ETL job logs** for record counts and failure messages
* Validate **incremental loads and late-arriving data**
* Automate completeness checks using scripts or dashboards
* Establish **alerts for missing data partitions**
* Cross-validate **lookup/reference tables** for completeness

---

### **6. Challenges**

| Challenge                 | Description                                                 |
| ------------------------- | ----------------------------------------------------------- |
| **Large Data Volumes**    | Row count comparison may be slow and resource-intensive     |
| **Partial File Loads**    | Files may be processed partially without failure indication |
| **Truncated Columns**     | Long strings or special characters may get silently cut off |
| **Missing Delta Records** | Incremental changes may not be captured properly            |
| **Nulls Misinterpreted**  | Legitimate nulls may be flagged as errors or vice versa     |

---
