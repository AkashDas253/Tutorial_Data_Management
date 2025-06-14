## **Galaxy Schema (Fact Constellation Schema)**

---

### **1. Definition**

The **Galaxy Schema**, also known as the **Fact Constellation Schema**, is a complex data warehouse schema that contains **multiple fact tables** sharing **common dimension tables**. It models multiple business processes or subject areas within a single schema.

---

### **2. Components**

| Component                | Description                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------- |
| **Fact Tables**          | Multiple fact tables representing different business processes or events                     |
| **Conformed Dimensions** | Dimension tables shared by multiple fact tables to ensure consistency across different facts |

---

### **3. Characteristics**

* Multiple fact tables interconnected by shared dimension tables
* Uses conformed dimensions for consistent reporting
* Supports complex business models involving various processes
* Dimensions can be denormalized or normalized
* Can represent multiple star schemas combined into one schema

---

### **4. Advantages**

* **Reusability:** Dimensions reused across multiple fact tables
* **Flexibility:** Models complex and diverse business processes in one schema
* **Consistency:** Shared dimensions ensure uniformity in data interpretation
* **Scalability:** Easy to extend with additional facts or dimensions

---

### **5. Disadvantages**

* **Complexity:** More complex to design, understand, and maintain
* **Query performance:** Queries involving multiple fact tables can require complex joins and may be slower
* **ETL Complexity:** More complex data loading and management processes

---

### **6. Use Cases**

* Enterprises with multiple business processes needing integrated reporting
* Scenarios where different fact tables share common dimensions (e.g., sales and inventory sharing customer and product dimensions)
* Large-scale data warehouses requiring modular and scalable schema design

---

### **7. Comparison with Star and Snowflake Schemas**

| Feature           | Galaxy Schema               | Star Schema           | Snowflake Schema                          |
| ----------------- | --------------------------- | --------------------- | ----------------------------------------- |
| Fact Tables       | Multiple                    | Single                | Single                                    |
| Dimension Tables  | Shared (conformed)          | Unique per fact table | Normalized dimensions                     |
| Complexity        | High                        | Low                   | Medium                                    |
| Query Performance | Moderate to slow            | Fast                  | Slower                                    |
| Use Case          | Multiple business processes | Simple reporting      | Complex hierarchies, storage optimization |

---

### **8. Example Diagram**

```
        Customer_Dim          Product_Dim
              \                  /
               \                /
           Fact_Sales        Fact_Inventory
               |                  |
             Time_Dim           Location_Dim
```

---

### **9. Best Practices**

* Use **conformed dimensions** consistently across fact tables
* Carefully design ETL processes for each fact table and shared dimensions
* Optimize queries with proper indexing on foreign keys
* Document schema relationships clearly for easier maintenance

---
