## **Nulls in Facts**

---

### **1. What are Nulls in Fact Tables?**

* **Null values** in fact tables indicate **missing, unknown, or inapplicable data** for a particular fact or measure.
* Nulls can appear in **measure columns** or **foreign key columns** (dimension references).

---

### **2. Causes of Nulls in Facts**

* Data not available or not collected at the time of ETL.
* Certain measures do not apply for specific records.
* Errors or gaps in source systems.
* Late arriving data or delayed updates.
* Incomplete or optional events.

---

### **3. Handling Nulls in Fact Tables**

| Aspect              | Handling Strategy                                                                                                                                            |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Measures**        | - Use default values like 0 if measure logically can be zero.<br>- Use NULL if absence of data conveys meaning.<br>- Document the meaning of NULL carefully. |
| **Foreign Keys**    | - Use a special "Unknown" or "Not Applicable" surrogate key in dimension tables.<br>- Avoid NULL foreign keys to maintain referential integrity.             |
| **Queries/Reports** | - Use functions like `COALESCE()` to replace NULLs in aggregations.<br>- Handle NULLs explicitly to avoid incorrect sums or averages.                        |

---

### **4. Impact of Nulls on Analysis**

* Nulls can cause **incorrect aggregations** if not handled (e.g., SUM ignoring NULLs vs zeros).
* May lead to **data quality issues** or misinterpretation.
* Important to differentiate between “no data” vs “zero value”.

---

### **5. Best Practices**

* Prefer **default or sentinel values** over NULL for foreign keys.
* Document NULL semantics clearly for measures.
* Use ETL checks to minimize unexpected NULLs.
* Use data profiling to identify and address null patterns.

---

### **6. Example**

| Fact Table Column | Null Handling Example                           |
| ----------------- | ----------------------------------------------- |
| Sales\_Amount     | Null → 0 (if no sale, zero amount)              |
| Discount\_Amount  | Null → 0 (if no discount applied)               |
| Customer\_Key     | Null → use surrogate key for ‘Unknown Customer’ |

---
