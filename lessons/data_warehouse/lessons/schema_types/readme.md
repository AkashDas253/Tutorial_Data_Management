## **Schema Types in Data Warehousing**

---

### **1. Star Schema**

* **Definition:** A simple schema with a central fact table linked directly to multiple denormalized dimension tables.
* **Characteristics:**

  * Denormalized dimension tables
  * Simple structure, easy to understand
  * Fast query performance due to fewer joins
* **Use Cases:** Fast querying, straightforward reporting, BI dashboards
* **Pros:** Simple, fast queries, easy for users
* **Cons:** Data redundancy, larger storage

---

### **2. Snowflake Schema**

* **Definition:** An extension of star schema where dimension tables are normalized into multiple related tables.
* **Characteristics:**

  * Normalized dimension tables
  * Complex schema with multiple joins
  * Reduced redundancy and storage
* **Use Cases:** Complex hierarchies, storage optimization, data integrity emphasis
* **Pros:** Reduced redundancy, better data integrity
* **Cons:** Slower queries, complex design

---

### **3. Galaxy Schema (or Fact Constellation Schema)**

* **Definition:** Multiple fact tables share dimension tables; used to model complex data marts.
* **Characteristics:**

  * Multiple fact tables interconnected
  * Shared conformed dimension tables
  * Combines features of star schemas
* **Use Cases:** Complex business models needing multiple fact tables
* **Pros:** Flexibility, reuse of dimensions
* **Cons:** More complex than star or snowflake

---

### **4. Flat Schema**

* **Definition:** All data stored in a single table without fact/dimension separation.
* **Characteristics:**

  * Simple, no joins
  * Not scalable or efficient for large data
* **Use Cases:** Small datasets, simple reporting
* **Pros:** Easy to query, no joins
* **Cons:** Poor performance and maintenance for large data

---

### **5. Data Vault Schema**

* **Definition:** A hybrid approach combining normalization and denormalization, designed for agility and historical tracking.
* **Characteristics:**

  * Separate hubs (keys), links (relationships), and satellites (descriptive data)
  * Designed for scalability and auditability
* **Use Cases:** Agile, scalable enterprise data warehouses
* **Pros:** Flexibility, historical tracking, auditability
* **Cons:** Complexity in design and querying

---

### **Summary Table**

| Schema Type       | Description                        | Dimension Tables        | Fact Tables | Pros                    | Cons                    |
| ----------------- | ---------------------------------- | ----------------------- | ----------- | ----------------------- | ----------------------- |
| Star Schema       | Central fact + denormalized dims   | Denormalized            | Single      | Simple, fast queries    | Data redundancy         |
| Snowflake Schema  | Normalized dimension tables        | Normalized              | Single      | Reduced redundancy      | Slower queries, complex |
| Galaxy Schema     | Multiple facts + shared dimensions | Denormalized/Normalized | Multiple    | Flexible, reusable dims | Complex schema          |
| Flat Schema       | Single table, no separation        | None                    | None        | Simple to query         | Not scalable            |
| Data Vault Schema | Hubs, links, satellites            | Normalized              | Multiple    | Scalable, auditable     | Complex to design/query |

---
