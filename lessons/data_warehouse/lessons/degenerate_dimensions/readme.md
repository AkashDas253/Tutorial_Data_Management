## Degenerate Dimensions

---

### 1. Definition

A **Degenerate Dimension (DD)** is a **dimension attribute** that is stored in the **fact table** but **does not have its own dimension table**. It typically originates from **transaction identifiers** or other operational control numbers.

---

### 2. Characteristics

| Feature                          | Description                                                   |
| -------------------------------- | ------------------------------------------------------------- |
| Exists in Fact Table             | The attribute resides in the fact table only                  |
| No Corresponding Dimension Table | Not associated with a separate dimension table                |
| Non-descriptive                  | Doesn't contain additional descriptive attributes             |
| Unique Identifiers               | Often represents document numbers like invoice\_id, order\_id |
| Helps Trace Transactions         | Useful for detailed reporting and tracing back to source      |

---

### 3. Purpose

* To maintain **granularity of data** without creating unnecessary dimension tables
* Useful for **auditing, tracing, and operational reporting**
* Avoids bloating the schema with one-column dimensions

---

### 4. Examples

| Fact Table Attribute | Description                                     |
| -------------------- | ----------------------------------------------- |
| invoice\_number      | Unique number for each invoice                  |
| order\_number        | Unique order tracking code                      |
| transaction\_id      | Identifier for financial or retail transactions |

These are typically **not joined** with dimension tables because they don’t describe anything other than the transaction itself.

---

### 5. When to Use

* When an identifier **has no descriptive attributes**
* When the identifier is **only used for tracing, not analysis**
* When normal dimension modeling would add **unnecessary complexity**

---

### 6. Comparison with Other Dimensions

| Aspect               | Degenerate Dimension       | Normal Dimension        |
| -------------------- | -------------------------- | ----------------------- |
| Stored in Fact Table | Yes                        | No (separate table)     |
| Has Attributes       | No                         | Yes                     |
| Descriptive Use      | Low                        | High                    |
| Common Use Case      | Transaction ID, Invoice No | Product, Customer, Time |

---

### 7. Best Practices

* Use only when there’s **no additional descriptive data** for the identifier
* Ensure uniqueness to preserve **granularity of facts**
* Avoid unnecessary joins by **not converting it into a dimension table**
* Document degenerate dimensions clearly for reporting clarity

---

### 8. Misuse to Avoid

* **Don’t create** a dimension table with just a surrogate and one business key if there are no attributes
* **Don’t overload** the fact table with multiple such keys unless necessary for traceability

---
