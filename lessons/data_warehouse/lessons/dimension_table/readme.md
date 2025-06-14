## **Dimension Table**

---

### **1. Definition**

A **Dimension Table** is a descriptive table in a data warehouse schema that contains **contextual (categorical or textual)** information to interpret and give meaning to the quantitative facts stored in the **Fact Table**.

---

### **2. Purpose**

* Provides **descriptive context** to numerical data in fact tables
* Supports **grouping**, **filtering**, and **labeling** in analysis
* Enables **OLAP operations** like slice, dice, drill-down, and roll-up
* Supports **hierarchies** and multi-level analysis

---

### **3. Key Characteristics**

| Characteristic        | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| **Descriptive**       | Contains textual or categorical information about entities or events |
| **Low cardinality**   | Has fewer rows than fact tables                                      |
| **Denormalized**      | Often denormalized for query performance (typical in Star Schemas)   |
| **Has hierarchies**   | Supports multi-level drill-downs (e.g., Year > Quarter > Month)      |
| **Referenced via FK** | Connected to fact tables via foreign keys                            |
| **Stable data**       | Changes infrequently; changes managed via Slowly Changing Dimensions |

---

### **4. Components**

| Component       | Description                                                            |
| --------------- | ---------------------------------------------------------------------- |
| **Primary Key** | Uniquely identifies each record; usually a surrogate key for stability |
| **Attributes**  | Descriptive fields such as names, categories, dates, etc.              |
| **Hierarchies** | Multi-level groupings to enable drill-down and roll-up                 |
| **Metadata**    | Optional audit or tracking fields                                      |

---

### **5. Examples**

| Table Name     | Key Attributes                              |
| -------------- | ------------------------------------------- |
| `Time_Dim`     | year, quarter, month, day\_name             |
| `Product_Dim`  | product\_name, brand, category, subcategory |
| `Customer_Dim` | customer\_name, age\_group, region          |
| `Location_Dim` | city, state, country                        |

---

### **6. Types of Dimensions**

| Type                                | Description                                                                     |
| ----------------------------------- | ------------------------------------------------------------------------------- |
| **Conformed Dimension**             | Shared across multiple fact tables for consistency (e.g., Time, Customer)       |
| **Junk Dimension**                  | Combines unrelated low-cardinality flags or indicators into one table           |
| **Degenerate Dimension**            | Keys stored in fact table itself (e.g., invoice number)                         |
| **Role-Playing Dimension**          | Same dimension table used in different contexts (e.g., Order Date vs Ship Date) |
| **Slowly Changing Dimension (SCD)** | Manages changes in dimension attributes over time                               |

---

### **7. Slowly Changing Dimensions (SCD) Types**

| Type       | Behavior                                            |
| ---------- | --------------------------------------------------- |
| **Type 0** | No changes allowed (static/fixed dimension)         |
| **Type 1** | Overwrites old attribute values                     |
| **Type 2** | Creates a new row with versioning to track history  |
| **Type 3** | Adds new columns to track previous attribute values |

---

### **8. Surrogate Keys**

* Used as **primary keys** to uniquely identify dimension rows
* Replace natural/business keys for stability and to support SCDs
* Are typically integers, system-generated, and immutable

---

### **9. Design Best Practices**

* Use **surrogate keys** for dimension tables
* Prefer **denormalized design** (star schema) for performance unless snowflake schema is required
* Define **clear attribute hierarchies** for drill-down/roll-up
* Plan SCD handling according to business needs
* Index commonly filtered columns for query speed
* Maintain **data quality:** minimize nulls and keep data consistent
* Manage historical data carefully to preserve analytic integrity

---

### **10. Challenges**

* Handling updates and historical changes in dimension data
* Balancing granularity and size of dimension tables
* Ensuring surrogate key consistency with fact tables
* Designing meaningful hierarchies without complexity overload

---
