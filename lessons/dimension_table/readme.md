## 📘 Dimension Table in Data Warehousing

---

### **Definition**

A **Dimension Table** is a descriptive table in a data warehouse schema that contains **contextual (categorical or textual)** information to interpret facts stored in the **Fact Table**.

---

### **Purpose**

- Provides **descriptive context** to numerical data in the fact table  
- Supports **grouping**, **filtering**, and **labeling** in analysis  
- Enables **OLAP operations** like slice, dice, drill-down, and roll-up  

---

### **Key Characteristics**

| Characteristic             | Description |
|----------------------------|-------------|
| **Descriptive**            | Contains textual or categorical information |
| **Low cardinality**        | Fewer rows compared to fact table |
| **Denormalized**           | Often denormalized for performance (Star Schema) |
| **Has hierarchies**        | Supports multi-level drill-down (e.g., Year → Quarter → Month) |
| **Referenced via FK**      | Linked to the fact table via foreign keys |

---

### **Components of a Dimension Table**

| Component         | Description |
|------------------|-------------|
| **Primary Key**   | Uniquely identifies each record (often a surrogate key) |
| **Attributes**    | Descriptive fields (e.g., product_name, customer_age) |
| **Hierarchies**   | Multi-level data groupings (e.g., Country → State → City) |
| **Metadata**      | Optional fields for tracking or audit |

---

### **Examples of Dimension Tables**

| Table Name         | Key Attributes |
|--------------------|----------------|
| `Time_Dim`         | year, quarter, month, day_name |
| `Product_Dim`      | product_name, brand, category, subcategory |
| `Customer_Dim`     | customer_name, age_group, region |
| `Location_Dim`     | city, state, country |

---

### **Types of Dimensions**

| Type                   | Description |
|------------------------|-------------|
| **Conformed Dimension** | Shared across multiple fact tables (e.g., Time, Customer) |
| **Junk Dimension**      | Combines unrelated flags and indicators into one table |
| **Degenerate Dimension** | Stored in the fact table itself (e.g., invoice number) |
| **Role-Playing Dimension** | Same dimension used in multiple roles (e.g., Order Date, Ship Date from Time) |
| **Slowly Changing Dimension (SCD)** | Manages changes in dimension values over time |

---

### **Slowly Changing Dimensions (SCD)**

| Type   | Behavior |
|--------|----------|
| **Type 0** | No changes allowed (fixed) |
| **Type 1** | Overwrites old data |
| **Type 2** | Creates new record for change (with versioning) |
| **Type 3** | Adds new column for previous value |

---

### **Best Practices**

- Use **surrogate keys** as primary keys  
- Avoid unnecessary normalization unless using Snowflake Schema  
- Clearly define **attribute hierarchies**  
- Design to support **SCDs** based on business needs  
- Index frequently queried columns  
- Limit nulls and ensure data quality (clean and complete)

---
