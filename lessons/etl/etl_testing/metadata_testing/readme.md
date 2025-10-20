## **Metadata Testing**

---

### **Overview**

**Metadata Testing** ensures that the **metadata (data about data)** in the data warehouse or ETL process is **accurate, consistent, and aligned** with business and technical requirements. Metadata includes **table structures, column definitions, data types, constraints, indexes, relationships, and business rules** documented for ETL and reporting.

---

### **Objectives**

* Validate **schema consistency** between source, staging, and target
* Verify **data types and lengths** match specifications
* Confirm **column names, table names, and aliases** are correct
* Ensure **primary keys, foreign keys, and constraints** are implemented as designed
* Check **indexes and partitions** for performance and design compliance
* Validate **business metadata**, e.g., descriptions, data lineage, source-to-target mappings
* Ensure **metadata changes are tracked and synchronized** across environments

---

### **1. Key Metadata Components to Test**

| Component                     | Description                                                    |
| ----------------------------- | -------------------------------------------------------------- |
| **Table and Column Names**    | Correct naming conventions and no mismatches                   |
| **Data Types & Lengths**      | Correct types (int, varchar, date, etc.) and field sizes       |
| **Constraints**               | Primary keys, foreign keys, unique constraints, NOT NULL rules |
| **Indexes and Partitions**    | Properly created for performance and query optimization        |
| **Default Values**            | Defaults as per design                                         |
| **Source-to-Target Mappings** | Accurate mappings between source and target columns            |
| **Data Lineage**              | Traceability of data movement and transformation               |

---

### **2. Sample Test Scenarios**

| Test Case ID | Scenario                      | Target Metadata       | Validation Rule                          |
| ------------ | ----------------------------- | --------------------- | ---------------------------------------- |
| TC\_MD\_001  | Verify table existence        | Customer\_dim         | Table must exist in target DB            |
| TC\_MD\_002  | Validate column names         | Customer\_dim columns | Names must match spec exactly            |
| TC\_MD\_003  | Validate data types           | Order\_fact columns   | Data types must match design doc         |
| TC\_MD\_004  | Check primary key constraints | Customer\_dim         | PK constraint on customer\_id must exist |
| TC\_MD\_005  | Check indexes                 | Sales\_fact           | Index on order\_date must be created     |
| TC\_MD\_006  | Validate default values       | status column         | Default value 'Active' must be set       |

---

### **3. Tools & Techniques**

| Tool/Method                  | Use Case                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| **Database Catalog Queries** | Query system tables to check schema and constraints          |
| **ETL Documentation**        | Source-to-target mapping documents and metadata repositories |
| **Data Modeling Tools**      | ER diagrams and metadata diagrams                            |
| **Automation Tools**         | Tools like Informatica Metadata Manager, Talend, Collibra    |
| **SQL Queries**              | Check constraints, indexes, and column properties            |

---

### **4. Sample SQL Queries**

**List tables in schema**

```sql
SELECT table_name FROM information_schema.tables WHERE table_schema='target_schema';
```

**List columns with data types**

```sql
SELECT column_name, data_type, character_maximum_length
FROM information_schema.columns
WHERE table_name='customer_dim';
```

**Check primary key constraints**

```sql
SELECT constraint_name, column_name 
FROM information_schema.key_column_usage 
WHERE table_name='customer_dim' AND constraint_name LIKE 'pk_%';
```

**Check indexes**

```sql
SHOW INDEX FROM sales_fact;
```

---

### **5. Best Practices**

* Maintain up-to-date **metadata repository** for all ETL objects
* Align **metadata testing with business rules and technical specs**
* Automate metadata validation during CI/CD pipelines
* Version control metadata definitions and changes
* Document and monitor **metadata drift** across environments
* Include metadata checks in regression and release testing

---

### **6. Challenges**

| Challenge                   | Description                                                     |
| --------------------------- | --------------------------------------------------------------- |
| **Metadata Drift**          | Changes in source or target schema without synchronized updates |
| **Incomplete Metadata**     | Missing documentation or inconsistent mappings                  |
| **Complex Transformations** | Difficult to trace lineage for derived columns                  |
| **Environment Differences** | Schema differences between DEV, QA, PROD                        |

---
