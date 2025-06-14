## **Facts**

---

### **1. What are Facts?**

**Facts** are **measurable, quantitative data** representing business events stored in the **fact table** of a data warehouse. They are used for **analysis and reporting**.

---

### **2. Key Characteristics of Facts**

| Attribute          | Description                                                           |
| ------------------ | --------------------------------------------------------------------- |
| **Quantitative**   | Represent numeric values (e.g., sales, profit, quantity)              |
| **Additive**       | Can be summed up across dimensions (e.g., revenue)                    |
| **Grain-specific** | Tied to the level of detail in the fact table (e.g., per transaction) |
| **Foreign Keys**   | Link to dimension tables                                              |

---

### **3. Types of Facts**

| Type                     | Description                                       | Example                           |
| ------------------------ | ------------------------------------------------- | --------------------------------- |
| **Additive**             | Can be aggregated across all dimensions           | Sales Amount, Units Sold          |
| **Semi-Additive**        | Can be aggregated across some dimensions, not all | Account Balance (not across time) |
| **Non-Additive**         | Cannot be aggregated                              | Ratios, Percentages               |
| **Derived (Calculated)** | Computed from other facts or columns              | Profit = Revenue – Cost           |

---

### **4. Types of Fact Tables**

| Type                      | Description                                                             | Example                   |
| ------------------------- | ----------------------------------------------------------------------- | ------------------------- |
| **Transactional**         | Captures individual events at fine grain                                | Each product sale         |
| **Snapshot**              | Periodic summary at regular intervals                                   | Monthly inventory levels  |
| **Accumulating Snapshot** | Tracks metrics over a process lifecycle (with milestones)               | Order-to-shipment process |
| **Factless**              | No measurable data; only foreign keys to represent events or conditions | Attendance, Enrollment    |

---

### **5. Fact Table Design Considerations**

| Concept                  | Explanation                                                  |
| ------------------------ | ------------------------------------------------------------ |
| **Grain**                | Defines the lowest level of detail (e.g., per day, per sale) |
| **Foreign Keys**         | Connect fact to each dimension                               |
| **Surrogate Keys**       | Used instead of natural keys for flexibility and performance |
| **Degenerate Dimension** | Text attributes like invoice number directly in fact table   |

---

### **6. Granularity of Fact**

* Specifies the **level of detail** stored (e.g., per transaction, per day)
* Affects storage size and aggregation capability
* **Finer grain = more detail but larger size**

---

### **7. Measures vs. Dimensions in Fact Table**

| Type           | Description                            | Examples                |
| -------------- | -------------------------------------- | ----------------------- |
| **Measures**   | Numerical data for analysis            | Revenue, Quantity       |
| **Dimensions** | Contextual data for slicing and dicing | Date, Customer, Product |

---

### **8. Fact Table Indexing**

* Often indexed by date and foreign keys
* Optimizes query performance

---

### **9. Examples of Facts**

| Business Area | Facts                                |
| ------------- | ------------------------------------ |
| Sales         | Revenue, Quantity, Discount, Tax     |
| Finance       | Account Balance, Interest, Profit    |
| Marketing     | Clicks, Impressions, Conversion Rate |
| Supply Chain  | Inventory Count, Shipment Cost       |

---

### **10. Best Practices**

* Define clear grain before designing
* Avoid storing calculated facts unless needed
* Include only relevant measures
* Ensure consistency across data marts

---
