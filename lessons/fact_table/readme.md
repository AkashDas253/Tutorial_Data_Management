## 📘 Fact Table in Data Warehousing

---

### **Definition**

A **Fact Table** is the central table in a star or snowflake schema of a data warehouse. It stores **quantitative data (measures)** for analysis and contains **foreign keys** referencing associated **dimension tables**.

---

### **Purpose**

- Stores business process **metrics** (e.g., sales amount, units sold)
- Enables **OLAP operations** (aggregation, slicing, dicing)
- Acts as the core for **schema joins** and analytical queries

---

### **Key Characteristics**

| Characteristic            | Description |
|---------------------------|-------------|
| **Contains measures**     | Numeric values for aggregation (SUM, AVG, etc.) |
| **Contains foreign keys** | References to dimension tables |
| **Large volume**          | Can have millions or billions of rows |
| **High granularity**      | Level of detail determined by the business need |
| **Additive or semi-additive** | Measures can often be aggregated over dimensions |

---

### **Components of a Fact Table**

| Component         | Description |
|------------------|-------------|
| **Fact/Measure**  | Numeric data such as revenue, cost, quantity |
| **Foreign Keys**  | Link to dimension tables (e.g., product_id, time_id) |
| **Surrogate Key** | Optional primary key unique to each fact row |
| **Metadata Columns** | Optional columns for audit or tracking (e.g., load date) |

---

### **Types of Facts**

| Type               | Description |
|--------------------|-------------|
| **Additive**        | Can be summed across all dimensions (e.g., sales amount) |
| **Semi-additive**   | Can be summed across some dimensions (e.g., balance over time) |
| **Non-additive**    | Cannot be summed (e.g., ratios, percentages) |
| **Derived**         | Calculated from other measures (e.g., profit = revenue - cost) |

---

### **Types of Fact Tables**

| Type               | Description |
|--------------------|-------------|
| **Transactional Fact Table** | Contains data at the finest level (e.g., every sale) |
| **Snapshot Fact Table**       | Periodic data snapshots (e.g., monthly account balance) |
| **Accumulating Fact Table**   | Tracks progress of processes (e.g., order lifecycle) |

---

### **Grain of the Fact Table**

- **Definition**: The level of detail in each record
- **Examples**:
  - Per transaction
  - Per customer per day
  - Per product per month
- Must be **defined clearly and consistently**

---

### **Best Practices**

- Define **grain** before identifying facts and dimensions
- Use **surrogate keys** for better performance and history tracking
- Keep **measure columns atomic** (not derived unless needed)
- Normalize or denormalize based on schema type
- Include **audit metadata** (load date, source, versioning)

---
