## **Nulls in Dimensions**

---

### **1. What are Nulls in Dimensions?**

**Null values** in dimension tables represent **missing, unknown, or inapplicable data** in one or more dimension attributes.

---

### **2. Why Nulls Occur in Dimensions**

* Data not captured or unavailable from source systems
* Late-arriving data (data arrives after fact records)
* Optional or irrelevant attributes for certain dimension members
* Errors or gaps in data extraction or transformation

---

### **3. Problems with Nulls in Dimensions**

* Joins between fact and dimension tables may fail or be inconsistent
* Reporting and aggregation errors or confusion
* Filtering and grouping may not behave as expected
* Difficulty in maintaining data quality and consistency

---

### **4. Best Practices to Handle Nulls in Dimensions**

| Practice                                   | Description                                                                                                                        |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Use Default or Unknown Members**         | Create a special dimension row representing unknown or missing values (e.g., “Unknown Customer”) with a surrogate key like 0 or -1 |
| **Avoid Null Foreign Keys in Fact Table**  | Facts should reference a valid surrogate key, never NULL                                                                           |
| **Populate Null Attributes with Defaults** | Use default strings such as “Not Available”, “Unknown”, or “N/A”                                                                   |
| **Data Cleansing During ETL**              | Identify and handle missing data in ETL process before loading                                                                     |
| **Late Arriving Dimensions (LAD)**         | Add dimension rows later if data arrives after facts (also called “inferred members”)                                              |

---

### **5. Example: Unknown Dimension Member**

| Surrogate\_Key | Customer\_Name   | Region     | Customer\_Type |
| -------------- | ---------------- | ---------- | -------------- |
| 0              | Unknown Customer | Unknown    | Unknown        |
| 1              | John Doe         | North East | Retail         |
| 2              | Jane Smith       | South West | Wholesale      |

In the fact table, if the customer is unknown, foreign key = 0 instead of NULL.

---

### **6. Benefits of Avoiding Nulls**

* Ensures referential integrity
* Simplifies query logic and reporting
* Consistent and meaningful analysis results
* Easier troubleshooting and data quality checks

---

### **7. Summary**

* Nulls in dimension attributes cause data quality and analytical issues
* Use “Unknown” or default rows to replace nulls
* Never allow null foreign keys in fact tables
* Handle missing data proactively during ETL

---
