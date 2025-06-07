## **Dimensions**

---

### **1. What are Dimensions?**

**Dimensions** are **descriptive, textual attributes** that provide **context** to the measurable facts in a **fact table**. They allow users to **slice, dice, filter, and group** data for analysis.

---

### **2. Key Characteristics of Dimensions**

| Attribute              | Description                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| **Descriptive**        | Contains textual or categorical data (e.g., Product Name, Region) |
| **Denormalized**       | Usually flattened for performance and readability                 |
| **Connected to Facts** | Joined to fact table via **foreign key → surrogate key**          |
| **Hierarchical**       | Often contain levels (e.g., Country → State → City)               |
| **Used in Filtering**  | Applied in WHERE, GROUP BY, and reporting visuals                 |

---

### **3. Types of Dimensions**

| Type                                | Description                                                        | Example                                      |
| ----------------------------------- | ------------------------------------------------------------------ | -------------------------------------------- |
| **Conformed Dimension**             | Shared across multiple fact tables or data marts                   | Date, Customer                               |
| **Junk Dimension**                  | Combines low-cardinality flags/indicators into a single dimension  | Yes/No flags (e.g., Promo Applied)           |
| **Degenerate Dimension**            | Exists in the fact table only as an identifier (no separate table) | Invoice Number                               |
| **Role-Playing Dimension**          | Same dimension used in different roles                             | Date used as Order Date, Ship Date           |
| **Slowly Changing Dimension (SCD)** | Tracks changes in dimensional attributes over time                 | Change in Customer Address or Marital Status |

---

### **4. Slowly Changing Dimensions (SCD)**

| Type       | Description                                   | Action Taken                   |
| ---------- | --------------------------------------------- | ------------------------------ |
| **Type 0** | Retain original data; ignore changes          | No update                      |
| **Type 1** | Overwrite old data                            | Replace with latest            |
| **Type 2** | Add a new row with versioning/timestamps      | Track full history             |
| **Type 3** | Add new column to store old and current value | Limited history (one previous) |

---

### **5. Common Dimension Examples**

| Domain     | Dimensions                           |
| ---------- | ------------------------------------ |
| Sales      | Customer, Product, Region, Time      |
| Healthcare | Patient, Doctor, Hospital, Diagnosis |
| Retail     | Store, Item, Promotion, Calendar     |
| HR         | Employee, Department, Job Title      |

---

### **6. Dimension Table Structure**

| Attribute         | Description                                  |
| ----------------- | -------------------------------------------- |
| **Surrogate Key** | Unique identifier for each row (primary key) |
| **Natural Key**   | Business identifier (e.g., Employee ID)      |
| **Attributes**    | Descriptive columns (e.g., Name, Gender)     |
| **Hierarchies**   | Defined paths (e.g., Category → Subcategory) |

---

### **7. Hierarchies in Dimensions**

* Used for **roll-up** and **drill-down** in OLAP analysis
* Example:

  * Date: Year → Quarter → Month → Day
  * Geography: Country → State → City

---

### **8. Dimension Table vs. Fact Table**

| Feature | Dimension Table                     | Fact Table                 |
| ------- | ----------------------------------- | -------------------------- |
| Content | Descriptive attributes              | Quantitative measures      |
| Size    | Smaller, fewer rows                 | Larger, many rows          |
| Key     | Surrogate (PK), referenced in facts | Foreign keys to dimensions |
| Usage   | Slicing, filtering, grouping        | Aggregation, summarization |

---

### **9. Best Practices**

* Use **surrogate keys** for joining
* Avoid **nulls** in dimension attributes
* Predefine **hierarchies** for OLAP use
* Track changes using appropriate **SCD types**
* Keep names and labels **user-friendly**

---
