## **Natural Key**

---

### **1. What is a Natural Key?**

A **natural key** is a type of **business key** that is derived from real-world data and uniquely identifies a record using existing attributes from the business domain. It is called “natural” because it exists naturally in the data without needing system-generated values.

---

### **2. Characteristics**

| Feature                | Description                                                              |
| ---------------------- | ------------------------------------------------------------------------ |
| **Derived from Data**  | Taken directly from business attributes or real-world information        |
| **Meaningful**         | Carries intrinsic business meaning (e.g., email, SSN, VIN)               |
| **May Change**         | Can change due to data corrections, business processes, or reassignments |
| **Composite Possible** | Can be a combination of multiple fields to ensure uniqueness             |
| **Used in OLTP**       | Commonly used as primary keys in operational systems                     |

---

### **3. Examples**

| Entity   | Natural Key Example                 | Description                         |
| -------- | ----------------------------------- | ----------------------------------- |
| Employee | Social Security Number (SSN)        | Unique government-issued identifier |
| Product  | SKU (Stock Keeping Unit)            | Code assigned to each product       |
| Vehicle  | VIN (Vehicle Identification Number) | Unique vehicle code                 |
| Customer | Email Address                       | Often used as a unique identifier   |

---

### **4. Natural Key vs Surrogate Key**

| Feature              | Natural Key                   | Surrogate Key                         |
| -------------------- | ----------------------------- | ------------------------------------- |
| **Origin**           | From real-world/business data | System-generated                      |
| **Business Meaning** | Yes                           | No                                    |
| **Stability**        | Can change                    | Immutable                             |
| **Complexity**       | Can be long or composite      | Usually simple integer                |
| **Visibility**       | User-facing and meaningful    | Not exposed to end users              |
| **Usage**            | OLTP and source systems       | Data warehouse and dimensional models |

---

### **5. Advantages**

* Easy for users to understand and recognize
* No additional key generation needed
* Can simplify integration with external systems

---

### **6. Disadvantages**

* Changes in natural keys require complex updates and history tracking
* May be composite and large, hurting performance in joins
* Risk of key collisions or duplicates due to business inconsistencies
* Not suitable for tracking historical changes in data warehouse (SCD Type 2)

---

### **7. Usage in Data Warehousing**

* Natural keys are used for **lookup** and **identification** during ETL
* Surrogate keys replace natural keys in the data warehouse as primary keys
* Helps maintain **conformed dimensions** across systems
* Supports data **integration and cleansing**

---

### **8. Best Practices**

* Use natural keys for **record matching** and **deduplication** in ETL
* Do **not** use natural keys as primary keys in dimensional models
* Monitor and manage changes in natural keys carefully
* Document natural key definitions and formats clearly

---
