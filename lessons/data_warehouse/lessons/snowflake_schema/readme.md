## **Snowflake Schema**

---

### **1. Definition**

A **Snowflake Schema** is a data warehouse schema design where dimension tables are **normalized** into multiple related tables, creating a structure that resembles a snowflake shape. It extends the star schema by further decomposing dimensions into sub-dimensions to reduce data redundancy.

---

### **2. Components**

| Component                 | Description                                                                                             |
| ------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Fact Table**            | Central table storing measurable, quantitative data (facts) along with foreign keys to dimension tables |
| **Normalized Dimensions** | Dimension tables split into multiple related tables to remove redundancy and organize hierarchies       |

---

### **3. Characteristics**

* Dimension tables are **normalized** into multiple related tables
* Reduces data redundancy and storage requirements
* More complex schema with multiple joins needed for queries
* Supports complex hierarchies and relationships within dimensions
* Usually involves multiple levels of dimension tables connected via foreign keys

---

### **4. Advantages**

* **Reduced data redundancy:** Normalization removes duplicate data in dimension tables
* **Improved data integrity:** Changes in one place propagate through related tables
* **Storage efficiency:** Less disk space used compared to denormalized star schema
* **Better representation of complex hierarchies:** Naturally models hierarchical relationships

---

### **5. Disadvantages**

* **Query performance:** More joins required, which can slow down query response time
* **Complexity:** Harder to understand and navigate for end users and analysts
* **Maintenance:** More complicated ETL and schema management due to multiple related tables

---

### **6. Use Cases**

* Large data warehouses with complex dimension hierarchies
* Environments where storage optimization is important
* Scenarios requiring strict data integrity and normalization

---

### **7. Comparison with Star Schema**

| Feature           | Snowflake Schema                       | Star Schema                    |
| ----------------- | -------------------------------------- | ------------------------------ |
| Dimension Tables  | Normalized (split into related tables) | Denormalized                   |
| Query Performance | Slower due to more joins               | Faster due to fewer joins      |
| Complexity        | More complex                           | Simpler                        |
| Storage           | Less storage due to normalization      | More storage due to redundancy |
| Maintenance       | More complex                           | Easier                         |

---

### **8. Example Diagram**

```
     Product_Category_Dim
             |
     Product_Subcategory_Dim
             |
        Product_Dim
             |
       Fact_Sales
             |
     Customer_Dim
             |
      Location_Dim
```

---

### **9. Best Practices**

* Normalize dimension tables only if necessary to reduce redundancy or support hierarchies
* Balance between normalization and query performance based on use case
* Use surrogate keys consistently across all dimension tables
* Optimize query plans by indexing key foreign keys and join columns
* Carefully design ETL processes to maintain referential integrity

---
