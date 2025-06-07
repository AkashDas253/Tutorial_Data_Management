## **Schemas in Data Warehouse**

---

### **1. What is a Schema in Data Warehouse?**

A **schema** is the **blueprint or structure** that defines how data is organized within the data warehouse. It determines how **fact** and **dimension** tables are related, how efficiently data can be queried, and how easily it supports business analysis.

---

### **2. Types of Schemas**

| Schema Type          | Description                                                                        |
| -------------------- | ---------------------------------------------------------------------------------- |
| **Star Schema**      | Central fact table with denormalized dimension tables                              |
| **Snowflake Schema** | Fact table with normalized, hierarchically structured dimension tables             |
| **Galaxy Schema**    | Multiple fact tables sharing conformed dimensions (also called Fact Constellation) |
| **Factless Schema**  | Fact table without measurable facts; tracks events or coverage                     |
| **Hybrid Schema**    | Combination of star and snowflake for balancing performance and normalization      |

---

### **3. Star Schema**

#### Structure:

* One **central fact table**
* Multiple **denormalized dimension tables** directly connected

#### Characteristics:

* Simplified design and faster query performance
* Easy for business users to understand
* Higher redundancy in dimension tables

#### Use Case:

* Retail sales analysis, simple analytical workloads

---

### **4. Snowflake Schema**

#### Structure:

* Central fact table
* **Normalized dimension tables** split into hierarchical structures

#### Characteristics:

* Reduces redundancy and improves data integrity
* More complex queries with multiple joins
* Requires more storage efficiency

#### Use Case:

* Systems needing consistent data integrity and reduced storage cost

---

### **5. Galaxy Schema (Fact Constellation)**

#### Structure:

* Multiple fact tables (e.g., Sales, Returns)
* **Shared conformed dimensions** (e.g., Date, Product)

#### Characteristics:

* Supports complex business processes
* Modular, scalable structure
* Complex design and maintenance

#### Use Case:

* Large enterprise with multiple domains (finance, sales, supply chain)

---

### **6. Factless Fact Schema**

#### Structure:

* Fact table **contains only foreign keys**
* No numeric fact measures

#### Characteristics:

* Used for tracking events or coverage
* Helps answer “what happened” or “what did not happen”

#### Use Case:

* Student attendance, promotional coverage, event tracking

---

### **7. Hybrid Schema**

#### Structure:

* Mix of star and snowflake patterns
* Some dimensions are normalized; others are denormalized

#### Characteristics:

* Balanced performance and storage
* Flexible structure for various scenarios

#### Use Case:

* Evolving systems that need to optimize performance and reduce redundancy

---

### **8. Comparison Table**

| Feature            | Star Schema  | Snowflake Schema  | Galaxy Schema    | Factless Schema         | Hybrid Schema      |
| ------------------ | ------------ | ----------------- | ---------------- | ----------------------- | ------------------ |
| Fact Table         | Single       | Single            | Multiple         | Present (no measures)   | Single or Multiple |
| Dimension Table    | Denormalized | Normalized        | Conformed shared | Denormalized            | Mixed              |
| Query Performance  | High         | Moderate          | Varies           | High                    | Balanced           |
| Storage Efficiency | Low          | High              | Moderate         | High                    | Moderate           |
| Complexity         | Low          | Medium            | High             | Low                     | Medium             |
| Best for           | Simpler DWs  | Storage-sensitive | Complex systems  | Event/coverage tracking | Flexible systems   |

---

### **9. Schema Selection Considerations**

| Factor                 | Recommendation   |
| ---------------------- | ---------------- |
| Simplicity & Speed     | Star Schema      |
| Storage Optimization   | Snowflake Schema |
| Cross-domain Analytics | Galaxy Schema    |
| Event Tracking         | Factless Schema  |
| Mixed Requirements     | Hybrid Schema    |

---
