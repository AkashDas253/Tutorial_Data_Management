## **Surrogate Key**

---

### **1. What is a Surrogate Key?**

A **surrogate key** is a **system-generated unique identifier** (usually an integer) used as the **primary key** in a table, especially in **dimension tables** in a data warehouse.

It replaces the **natural key** (business key) for consistency, performance, and historical tracking.

---

### **2. Characteristics**

| Feature             | Description                                |
| ------------------- | ------------------------------------------ |
| **Artificial Key**  | Not derived from application data          |
| **Numeric/Integer** | Typically auto-incremented integer         |
| **Immutable**       | Doesn't change even if source data changes |
| **Opaque**          | Has no business meaning                    |

---

### **3. Purpose in Dimensional Modeling**

| Use Case                            | Role of Surrogate Key                                                            |
| ----------------------------------- | -------------------------------------------------------------------------------- |
| **Link Fact to Dimension Tables**   | Acts as the foreign key in fact tables                                           |
| **Support SCD Type 2**              | Allows multiple versions of a record with different surrogate keys               |
| **Avoid Dependency on Source Keys** | Insulates the data warehouse from changes in operational keys                    |
| **Improve Query Performance**       | Faster joins on integers than on strings or compound keys                        |
| **Role-Playing Dimensions**         | Enables reuse of same dimension in different roles (e.g., order date, ship date) |
| **Conformed Dimensions**            | Ensures consistency across multiple fact tables using same dimension             |

---

### **4. Surrogate Key vs Natural Key**

| Feature       | Surrogate Key         | Natural Key                          |
| ------------- | --------------------- | ------------------------------------ |
| Source        | System-generated      | Comes from business/application data |
| Stability     | Never changes         | May change                           |
| Uniqueness    | Globally unique       | Unique only in context               |
| Meaning       | No business meaning   | Has business meaning                 |
| Preferred For | Data warehouses, SCDs | OLTP systems                         |

---

### **5. Generation Techniques**

| Method             | Description                                   |
| ------------------ | --------------------------------------------- |
| **Auto-increment** | Database-generated incremental number         |
| **UUID/GUID**      | Universally unique identifier                 |
| **ETL Tools**      | Generate surrogate keys during ETL processing |
| **Hash-based**     | Hash of natural key fields (less preferred)   |

---

### **6. Example**

#### Customer Dimension Table:

| Surrogate Key | Customer\_ID (Natural Key) | Name       | Region |
| ------------- | -------------------------- | ---------- | ------ |
| 1             | CUST1001                   | John Doe   | East   |
| 2             | CUST1002                   | Jane Smith | West   |

#### Fact Table:

| Sale\_ID | Customer\_Key (Surrogate) | Date\_Key | Amount |
| -------- | ------------------------- | --------- | ------ |
| 501      | 1                         | 20240601  | 200.00 |
| 502      | 2                         | 20240601  | 350.00 |

---

### **7. Benefits**

* Enables **Type 2 Slowly Changing Dimensions**
* Prevents **key collisions** from source systems
* Improves **join performance**
* Simplifies **data management** in ETL
* Decouples data warehouse design from source systems

---

### **8. Challenges**

* Requires **ETL logic** to generate and manage
* Needs **lookup logic** to map natural keys to surrogate keys
* Additional **metadata management** and surrogate key tracking

---

### **9. Best Practices**

| Best Practice                       | Description                                                           |
| ----------------------------------- | --------------------------------------------------------------------- |
| **Always use in dimension tables**  | Ensures stable and consistent joins                                   |
| **Avoid exposing surrogate keys**   | Don’t show them in reports or business-facing interfaces              |
| **Use integers for performance**    | Prefer `INT` over `UUID` for faster joins and indexing                |
| **Maintain mapping table**          | Track relationship between natural and surrogate keys                 |
| **Ensure atomic key assignment**    | Use transaction-safe or sequence-based generation to avoid duplicates |
| **Track versioning for SCD Type 2** | Use surrogate keys with version indicators and effective date columns |
| **Consistent across data marts**    | Helps maintain conformed dimensions and reuse of master data          |

---
