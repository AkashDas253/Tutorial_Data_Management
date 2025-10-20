## **Dimensional Modeling Process**

---

### **1. Objective**

The **dimensional modeling process** aims to design a schema that is:

* Intuitive for business users
* Optimized for performance
* Scalable for growing data
* Compatible with analytical tools

---

### **2. Key Steps in Dimensional Modeling Process**

| Step                            | Description                                                             |
| ------------------------------- | ----------------------------------------------------------------------- |
| **Choose the Business Process** | Identify a specific business operation to model (e.g., sales, orders)   |
| **Declare the Grain**           | Define the level of detail for each fact (e.g., daily sales by product) |
| **Identify the Dimensions**     | List descriptive entities (e.g., customer, product, time)               |
| **Identify the Facts**          | Determine numeric measures to analyze (e.g., quantity, revenue)         |
| **Design Schema**               | Create star, snowflake, or galaxy schema based on relationships         |
| **Handle SCD**                  | Define slowly changing dimension strategy for historical tracking       |
| **Add Surrogate Keys**          | Use system-generated keys for dimension linkage and consistency         |
| **Document and Validate**       | Ensure correctness, completeness, and ease of use                       |

---

### **3. Step-by-Step Breakdown**

#### **Choose the Business Process**

* Select a core business process to analyze
* Examples: Retail sales, inventory movement, shipment tracking

#### **Declare the Grain**

* Decide the lowest level of detail stored in the fact table
* Must be defined clearly before choosing dimensions and facts
* Examples:

  * One row per product per day
  * One row per transaction

#### **Identify the Dimensions**

* Extract the descriptive attributes needed for analysis
* Examples:

  * Time (year, quarter, month)
  * Product (category, brand)
  * Customer (region, type)

#### **Identify the Facts**

* Pick measurable, numeric data points (additive, semi-additive, non-additive)
* Examples:

  * Sales amount
  * Discount
  * Units sold

#### **Design the Schema**

* Choose appropriate schema:

  * **Star**: Simpler queries, denormalized
  * **Snowflake**: Normalized dimensions, reduced redundancy
  * **Galaxy**: Multiple fact tables sharing dimensions

#### **Handle Slowly Changing Dimensions (SCD)**

| SCD Type | Strategy                            |
| -------- | ----------------------------------- |
| Type 0   | No changes allowed                  |
| Type 1   | Overwrite old data                  |
| Type 2   | Add new row with versioning/history |
| Type 3   | Add new column for previous values  |

#### **Add Surrogate Keys**

* Replace natural keys with unique identifiers
* Helps with SCD, consistency, and indexing

#### **Document and Validate**

* Review:

  * Business rules
  * Query requirements
  * Joins and relationships
* Validate data accuracy and performance

---

### **4. Best Practices**

* Focus on **business requirements**, not just source system structure
* Always **declare grain first**
* Use **conformed dimensions** across multiple facts
* Ensure **consistent naming conventions**
* Avoid unnecessary normalization for performance

---

### **5. Output Artifacts**

* Logical schema diagram (star/snowflake/galaxy)
* Dimensional table specifications
* Mapping document for ETL
* Metadata catalog

---
