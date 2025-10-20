## **Business Key**

---

### **1. What is a Business Key?**

A **business key** (also called a **natural key**) is an attribute or set of attributes that **uniquely identifies a real-world entity** based on **business logic or rules**, not system-generated values. It exists in **source systems (OLTP)** and carries **meaningful information**.

---

### **2. Characteristics**

| Feature               | Description                                                 |
| --------------------- | ----------------------------------------------------------- |
| **Derived from Data** | Comes directly from business data or source systems         |
| **Meaningful**        | Carries semantic meaning (e.g., email, SSN, order number)   |
| **May Change**        | Not always stable over time due to business or data updates |
| **Visible to Users**  | Often used or seen by business users and stakeholders       |
| **Can be Composite**  | Sometimes requires multiple fields to ensure uniqueness     |

---

### **3. Examples**

| Entity   | Business Key           | Description                                      |
| -------- | ---------------------- | ------------------------------------------------ |
| Employee | `EMP_ID`, `SSN`        | Social Security Number (SSN) uniquely identifies |
| Product  | `Product_Code`         | SKU or product ID used in transactions           |
| Customer | `Email`, `Customer_ID` | Email or external system ID                      |
| Invoice  | `Invoice_Number`       | Uniquely identifies an invoice                   |

---

### **4. Business Key vs Surrogate Key**

| Feature            | Business Key                  | Surrogate Key              |
| ------------------ | ----------------------------- | -------------------------- |
| **Meaning**        | Has business meaning          | No business meaning        |
| **Source**         | Derived from application data | System-generated           |
| **Stability**      | May change                    | Stable and never changes   |
| **Length/Type**    | Often long or composite       | Usually short integers     |
| **Usage**          | OLTP, business reference      | Data warehouse primary key |
| **Human-readable** | Yes                           | No                         |

---

### **5. Purpose and Usage**

| Use Case                         | Role of Business Key                                  |
| -------------------------------- | ----------------------------------------------------- |
| **Source system operations**     | Used in CRUD operations in OLTP                       |
| **Reference in reports**         | Used for human-readable identification                |
| **ETL lookup and deduplication** | Helps find if record already exists                   |
| **Mapping surrogate keys**       | Used as input in mapping to surrogate keys during ETL |
| **Conformed dimensions**         | Acts as anchor when integrating data across sources   |

---

### **6. Challenges**

| Challenge                 | Description                                                  |
| ------------------------- | ------------------------------------------------------------ |
| **Data inconsistency**    | Different systems may use different formats or values        |
| **Change risk**           | Business keys can change due to user input or business rules |
| **Duplicates**            | Poor validation may lead to multiple rows with same key      |
| **Length and complexity** | Composite or long keys are inefficient in joins/indexing     |

---

### **7. Best Practices**

| Best Practice                         | Description                                                                |
| ------------------------------------- | -------------------------------------------------------------------------- |
| **Enforce uniqueness in source**      | Validate that business keys are truly unique                               |
| **Track history separately**          | Don’t rely on business keys to track changes (use surrogate keys for that) |
| **Use for deduplication in ETL**      | Lookup based on business key to detect existing records                    |
| **Avoid using as DW PK**              | Use surrogate keys in the warehouse; keep business keys as attributes      |
| **Keep human-readable and formatted** | Ensure clean, consistent, and parseable formatting                         |

---
