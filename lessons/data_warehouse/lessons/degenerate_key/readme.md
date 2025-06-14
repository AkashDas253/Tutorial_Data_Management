## **Degenerate Key**

---

### **1. What is a Degenerate Key?**

A **degenerate key** is a **dimension key stored in the fact table** that **does not have a corresponding dimension table**. It typically represents an identifier from the source system (like an invoice number or transaction ID) that is meaningful for reporting but does not require additional descriptive attributes.

---

### **2. Characteristics**

| Feature                       | Description                                          |
| ----------------------------- | ---------------------------------------------------- |
| **No Dimension Table**        | Exists only in the fact table, no separate dimension |
| **Source System Origin**      | Usually a transactional or operational system key    |
| **Meaningful to Business**    | Often visible and used by business users in reports  |
| **No Foreign Key Constraint** | Not linked to any dimension table                    |
| **Stored in Fact Table**      | Included as an attribute of the fact record          |

---

### **3. Examples**

| Fact Table Column | Description                      |
| ----------------- | -------------------------------- |
| Invoice Number    | Unique ID for each sales invoice |
| Order Number      | Transactional order identifier   |
| Transaction ID    | Unique ID of a payment or event  |

---

### **4. Purpose and Usage**

* Tracks **transactional identifiers** without needing a dimension table.
* Helps in **drilling down** or referencing back to the source system.
* Maintains **simpler schema** by avoiding unnecessary dimension tables.
* Provides **business context** directly in the fact table.

---

### **5. Differences from Other Keys**

| Key Type       | Has Dimension Table? | Location         | Usage                        |
| -------------- | -------------------- | ---------------- | ---------------------------- |
| Degenerate Key | No                   | Fact table only  | Transactional ID in facts    |
| Surrogate Key  | Yes                  | Dimension & Fact | Joins between facts and dims |
| Natural Key    | Yes                  | Dimension        | Business unique identifier   |

---

### **6. Benefits**

* Simplifies data warehouse design by reducing dimension tables.
* Retains important transactional identifiers for traceability.
* Improves query performance by avoiding extra joins.
* Makes fact tables self-descriptive with respect to transactions.

---

### **7. Considerations**

* Cannot store descriptive attributes — only the key itself.
* If descriptive data is needed, consider creating a dimension table.
* Should be indexed in fact tables for efficient filtering and lookup.

---
