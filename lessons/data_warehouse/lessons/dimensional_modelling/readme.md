## **Dimensional Modeling**

Dimensional modeling is a **data modeling technique** optimized for **data warehouse design** and **OLAP systems**, aiming to improve **query performance** and **understandability** of data.

---

### **1. Purpose**

* Organize data for analytical processing
* Make data intuitive and fast to retrieve
* Support slicing, dicing, drilling, and pivoting

---

### **2. Key Components**

| Component            | Description                                                    |
| -------------------- | -------------------------------------------------------------- |
| **Fact Tables**      | Store quantitative data for analysis (measurable events)       |
| **Dimension Tables** | Store descriptive attributes related to facts                  |
| **Measures**         | Numeric values in fact tables (e.g., sales amount)             |
| **Grain**            | Level of detail stored in the fact table                       |
| **Keys**             | Surrogate keys used to link dimension tables to the fact table |

---

### **3. Types of Tables**

#### **Fact Table**

* Contains **foreign keys** to dimension tables
* Stores **measures** (metrics)
* Types:

  * **Transactional Fact**: Fine-grained, event-based (e.g., sales)
  * **Snapshot Fact**: Periodic snapshot (e.g., monthly balance)
  * **Accumulating Fact**: Tracks lifecycle (e.g., order process)

#### **Dimension Table**

* Contains **attributes** to describe business entities
* Denormalized for performance
* Examples: Customer, Product, Time, Location

---

### **4. Schema Types**

| Schema                                     | Structure                                                     |
| ------------------------------------------ | ------------------------------------------------------------- |
| **Star Schema**                            | Central fact table with denormalized dimension tables         |
| **Snowflake Schema**                       | Normalized dimension tables (adds complexity but saves space) |
| **Galaxy Schema** / **Fact Constellation** | Multiple fact tables sharing dimension tables                 |

---

### **5. Dimensional Modeling Process**

* Choose the business process
* Declare the grain
* Identify dimensions
* Identify facts
* Design schema (Star/Snowflake)

---

### **6. Slowly Changing Dimensions (SCD)**

| Type   | Description                                   |
| ------ | --------------------------------------------- |
| Type 0 | No changes allowed                            |
| Type 1 | Overwrite old data                            |
| Type 2 | Add new row for each change (track history)   |
| Type 3 | Add new column for current and previous value |

---

### **7. Hierarchies in Dimensions**

* Define drill-down paths (e.g., Year → Quarter → Month → Day)
* Enable roll-up and drill-down analysis

---

### **8. Surrogate Keys**

* System-generated keys (integers)
* Used instead of natural keys for simplicity and performance

---

### **9. Degenerate Dimensions**

* Dimension values stored in the fact table itself (e.g., invoice number)
* No corresponding dimension table

---

### **10. Junk Dimensions**

* Combine unrelated flags or indicators into a single dimension table to reduce clutter

---

### **11. Role-Playing Dimensions**

* Single dimension used in multiple roles (e.g., Date dimension used for order\_date, ship\_date)

---

### **12. Conformed Dimensions**

* Shared across multiple fact tables or data marts for consistency (e.g., Customer dimension)

---

### **13. Factless Fact Tables**

* No measurable facts, only foreign keys
* Used for tracking events (e.g., student attendance)

---

### **14. Advantages**

* Faster querying
* Simpler reporting and analysis
* Intuitive to business users

---

### **15. Limitations**

* Denormalization can lead to redundancy
* Complex for handling frequent schema changes
* Not ideal for OLTP systems

---
