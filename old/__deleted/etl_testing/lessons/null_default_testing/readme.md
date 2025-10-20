## **Null and Default Testing**

---

### **Overview**

**Null Testing** and **Default Value Testing** ensure that the data loaded into the target system adheres to the **expected rules for nullability and default values**. This confirms that mandatory fields are **never null**, optional fields handle nulls correctly, and default values are applied where data is missing.

---

### **Objectives**

* Verify **mandatory columns do not contain nulls**
* Confirm **optional columns handle nulls as per requirements**
* Ensure **default values are set correctly** when source data is missing or null
* Detect **unexpected nulls or incorrect default assignments**
* Validate **data type compatibility** with null/default values

---

### **1. Null Testing**

| Scenario                                     | Description                                      |
| -------------------------------------------- | ------------------------------------------------ |
| Mandatory fields should never be null        | E.g., customer\_id, order\_id must have values   |
| Optional fields may have nulls               | E.g., middle\_name, secondary\_phone can be null |
| Nulls in primary or foreign keys are invalid | Referential integrity violations                 |
| Nulls in date/time fields                    | Should follow business logic (default date?)     |

---

### **2. Default Value Testing**

| Scenario                                                   | Description                         |
| ---------------------------------------------------------- | ----------------------------------- |
| Default values set when source is null or missing          | E.g., status = 'Active' if null     |
| Numeric fields default to zero or business-defined default | E.g., discount = 0 when missing     |
| String fields default to placeholder or empty string       | E.g., address = 'N/A'               |
| Date fields default to system date or specific date        | E.g., created\_date = current\_date |

---

### **3. Sample Test Scenarios**

| Test Case ID  | Scenario                    | Column       | Expected Result                 |
| ------------- | --------------------------- | ------------ | ------------------------------- |
| TC\_NULL\_001 | Mandatory field null check  | customer\_id | No nulls allowed                |
| TC\_NULL\_002 | Optional field null allowed | middle\_name | Null values allowed             |
| TC\_NULL\_003 | Null in foreign key         | product\_id  | No nulls allowed                |
| TC\_DEF\_001  | Default value for status    | status       | Null or missing set to 'Active' |
| TC\_DEF\_002  | Default numeric discount    | discount     | Null set to 0                   |

---

### **4. Tools & Techniques**

| Method                     | Usage                                                        |
| -------------------------- | ------------------------------------------------------------ |
| SQL queries                | `WHERE column IS NULL` or `WHERE column <> expected_default` |
| ETL tool validation rules  | Built-in checks during ETL load                              |
| Automated scripts (Python) | Scan data for null/default violations                        |
| Reports/Dashboards         | Monitor null/default statistics                              |

---

### **5. Sample SQL Snippets**

**Check for Nulls in mandatory columns**

```sql
SELECT * FROM target_table WHERE customer_id IS NULL;
```

**Check for incorrect default values**

```sql
SELECT * FROM target_table WHERE status IS NULL OR status <> 'Active';
```

**Set default value during ETL (example)**

```sql
SELECT
  customer_id,
  COALESCE(status, 'Active') AS status
FROM source_table;
```

---

### **6. Best Practices**

* Define **nullability and default rules clearly** in metadata or design docs
* Always validate **primary and foreign keys** for nulls
* Use **COALESCE/IFNULL** or ETL functions to handle defaults
* Monitor **unexpected nulls or missing defaults regularly**
* Test both **positive and negative scenarios** (nulls where allowed and not allowed)

---
