## **Star Schema**

---

### **1. Definition**

A **Star Schema** is a data warehouse schema design where a central **fact table** is connected directly to multiple **dimension tables**. The dimension tables are usually denormalized and contain descriptive attributes. The overall schema shape looks like a star, with the fact table at the center and dimension tables radiating outward.

---

### **2. Components**

| Component            | Description                                                                    |
| -------------------- | ------------------------------------------------------------------------------ |
| **Fact Table**       | Contains measurable, quantitative data (facts), and foreign keys to dimensions |
| **Dimension Tables** | Contain descriptive attributes that provide context for facts                  |

---

### **3. Characteristics**

* Simple and intuitive schema design
* Denormalized dimension tables for fast query performance
* Supports easy and fast **join** operations between fact and dimensions
* Fact table usually has a composite primary key made from foreign keys to dimension tables
* Dimensions provide rich context for facts (e.g., product, time, customer)

---

### **4. Advantages**

* **Query performance:** Denormalized dimensions reduce number of joins
* **Simplicity:** Easy for end users to understand and navigate
* **Fast aggregations:** Efficient for OLAP operations like roll-up, drill-down
* **Scalability:** Handles large volumes of data in fact tables effectively
* **Supports common BI queries** with simple joins between fact and dimension

---

### **5. Disadvantages**

* **Data redundancy:** Dimension tables are denormalized, leading to some duplicate data
* **Maintenance:** Updates to dimension tables can be complex due to denormalization
* **Lack of normalization:** Can cause anomalies during data load if not handled properly

---

### **6. Use Cases**

* Business Intelligence and Reporting systems
* Data marts focused on fast query performance
* Scenarios where ease of use and speed are prioritized over strict normalization

---

### **7. Comparison with Snowflake Schema**

| Feature           | Star Schema                    | Snowflake Schema                       |
| ----------------- | ------------------------------ | -------------------------------------- |
| Dimension Tables  | Denormalized                   | Normalized (split into related tables) |
| Query Performance | Faster due to fewer joins      | Slower due to more joins               |
| Complexity        | Simple                         | More complex                           |
| Storage           | More storage due to redundancy | Less storage                           |
| Maintenance       | Easier                         | More complex                           |

---

### **8. Example Diagram**

```
      Product_Dim
          |
Customer_Dim — Fact_Sales — Time_Dim
          |
     Store_Dim
```

---

### **9. Best Practices**

* Use surrogate keys in dimension tables for stability
* Keep dimension tables denormalized for query speed
* Design dimensions with clear hierarchies for drill-down
* Optimize indexing on fact table foreign keys and dimension attributes
* Handle slowly changing dimensions appropriately

---
