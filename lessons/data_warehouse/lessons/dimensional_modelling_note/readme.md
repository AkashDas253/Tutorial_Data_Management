## **Dimensional Modeling Node**

---

### **Definition**

Dimensional Modeling is a data design technique used in data warehousing to structure data for easy retrieval and analysis by organizing it into **facts** (numerical data) and **dimensions** (contextual data).

---

### **Purpose**

* Optimize for **query performance**, not data entry
* Enable **business-friendly, intuitive** data structure
* Support **OLAP** operations: slicing, dicing, drilling, pivoting

---

### **Core Components**

| Component           | Description                                                             |
| ------------------- | ----------------------------------------------------------------------- |
| **Fact Table**      | Central table with measurable, quantitative data (e.g., sales, revenue) |
| **Dimension Table** | Descriptive data to filter, group, or label facts (e.g., product, time) |
| **Grain**           | Level of detail (e.g., per transaction, per day)                        |
| **Measure**         | Numeric metrics (e.g., profit, units sold)                              |
| **Surrogate Key**   | Artificial primary key used for joining and tracking changes            |

---

### **Schemas**

| Schema Type          | Structure                                                                |
| -------------------- | ------------------------------------------------------------------------ |
| **Star Schema**      | Central fact table with directly connected denormalized dimension tables |
| **Snowflake Schema** | Dimension tables normalized into multiple related tables                 |
| **Galaxy Schema**    | Multiple fact tables sharing dimension tables (fact constellation)       |

---

### **Fact Table Types**

| Type              | Description                                                                 |
| ----------------- | --------------------------------------------------------------------------- |
| **Transactional** | Fine-grained, event-level data (e.g., each sale)                            |
| **Snapshot**      | Periodic summary data (e.g., daily balances)                                |
| **Accumulating**  | Lifecycle data (e.g., order to shipment process)                            |
| **Factless**      | No numeric data; used to record events or conditions (e.g., student signup) |

---

### **Dimension Table Features**

* Contain **attributes** used for analysis (e.g., product name, customer segment)
* **Denormalized** for performance
* Enable **hierarchies** (e.g., date → month → quarter → year)

---

### **Dimension Types**

| Type                        | Description                                                                |
| --------------------------- | -------------------------------------------------------------------------- |
| **Conformed Dimensions**    | Shared across different fact tables or data marts                          |
| **Role-Playing Dimensions** | Same dimension table used in different roles (e.g., order date, ship date) |
| **Junk Dimensions**         | Combine unrelated flags and indicators into one dimension                  |
| **Degenerate Dimensions**   | Appears in fact table, no separate dimension table (e.g., invoice number)  |

---

### **Slowly Changing Dimensions (SCD)**

| Type | Description                                   |
| ---- | --------------------------------------------- |
| 0    | No change allowed                             |
| 1    | Overwrite old value                           |
| 2    | Add new row with new surrogate key            |
| 3    | Add new column for current and previous value |

---

### **Dimensional Modeling Steps**

* Identify the business process to model
* Declare the grain
* Choose the facts
* Choose the dimensions
* Design schema (star/snowflake/galaxy)

---

### **Advantages**

* Fast query performance
* Easy to understand
* Simplified reporting and analysis
* Business-oriented structure

---

### **Disadvantages**

* Redundancy due to denormalization
* Not suitable for frequent updates
* Harder to maintain with schema changes

---

### **Use Cases**

* Data Warehousing
* OLAP cubes
* Business Intelligence dashboards
* Historical trend analysis

---
