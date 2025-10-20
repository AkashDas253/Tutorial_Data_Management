## **Schema Testing**

---

### **Overview**

**Schema Testing** verifies that the **database schema** (structure) of the data warehouse or ETL target system is **correct, complete, and aligns with design specifications**. It ensures tables, columns, data types, constraints, indexes, and relationships are properly created and maintained.

---

### **Objectives**

* Validate **existence of tables and views** as per design
* Confirm **correct column names, data types, sizes, and nullability**
* Verify **primary key, foreign key, unique, and check constraints**
* Check **indexes and partitions** for performance optimization
* Ensure **no extra or missing schema objects**
* Detect **schema drift** between environments (DEV, QA, PROD)

---

### **1. Key Components in Schema Testing**

| Component                    | What to Validate                                    |
| ---------------------------- | --------------------------------------------------- |
| Tables & Views               | Presence, naming conventions, and correct structure |
| Columns                      | Name, data type, size/length, nullable/not nullable |
| Primary Keys                 | Existence, uniqueness, and correct columns          |
| Foreign Keys                 | Relationships and referential integrity             |
| Unique Constraints           | No duplicate values in specified columns            |
| Check Constraints            | Business rule enforcement (e.g., age > 18)          |
| Indexes & Partitions         | Created for performance, proper usage               |
| Triggers & Stored Procedures | Presence and correctness for automated actions      |

---

### **2. Sample Test Scenarios**

| Test Case ID    | Scenario                        | Expected Result                                 |
| --------------- | ------------------------------- | ----------------------------------------------- |
| TC\_SCHEMA\_001 | Validate all expected tables    | All tables listed in design doc are present     |
| TC\_SCHEMA\_002 | Check column names and types    | Columns match design including types & size     |
| TC\_SCHEMA\_003 | Verify primary key on order\_id | Primary key exists and is enforced              |
| TC\_SCHEMA\_004 | Check foreign key constraints   | Foreign keys enforce correct parent-child links |
| TC\_SCHEMA\_005 | Verify index on date column     | Index exists on transaction\_date column        |
| TC\_SCHEMA\_006 | Validate NOT NULL constraints   | Mandatory columns disallow null values          |

---

### **3. Tools & Techniques**

| Tool/Method                 | Usage                                                         |
| --------------------------- | ------------------------------------------------------------- |
| **SQL Information Schema**  | Query metadata tables (`information_schema`) to check schema  |
| **DBMS Catalog Views**      | Use system-specific views (e.g., `DBA_CONSTRAINTS` in Oracle) |
| **Schema Comparison Tools** | Compare schemas between environments (Redgate, Liquibase)     |
| **Data Modeling Tools**     | ER diagrams to cross-check schema design                      |
| **Automated Scripts**       | Scripts to validate schema objects and constraints            |

---

### **4. Sample SQL Queries**

**List all tables in schema**

```sql
SELECT table_name FROM information_schema.tables WHERE table_schema='public';
```

**Get columns with data types and nullability**

```sql
SELECT column_name, data_type, is_nullable
FROM information_schema.columns
WHERE table_name='customer';
```

**Check primary keys**

```sql
SELECT constraint_name, column_name
FROM information_schema.key_column_usage
WHERE table_name='orders' AND constraint_name LIKE 'pk_%';
```

**Check foreign key constraints**

```sql
SELECT constraint_name, table_name, column_name, referenced_table_name, referenced_column_name
FROM information_schema.referential_constraints
JOIN information_schema.key_column_usage USING (constraint_name)
WHERE table_name='orders';
```

---

### **5. Best Practices**

* Maintain **updated schema documentation** aligned with business and technical designs
* Include schema validation in **ETL deployment and CI/CD pipelines**
* Automate schema comparison to detect drift across environments
* Test **both structural and relational integrity** (constraints, keys)
* Coordinate schema testing with **metadata and data validation testing** for full coverage

---
