## **Metadata in Data Warehousing**

---

### **1. What is Metadata?**

**Metadata** is **"data about data"** — it provides information that describes the **structure, usage, origin, and meaning** of data stored in the data warehouse.

---

### **2. Importance of Metadata**

* Helps **developers** understand system structure
* Assists **business users** in interpreting data
* Drives **ETL**, **reporting**, and **governance**
* Enables **data lineage**, **auditing**, and **troubleshooting**

---

### **3. Types of Metadata**

| Type                      | Description                                                          |
| ------------------------- | -------------------------------------------------------------------- |
| **Technical Metadata**    | Describes database objects, data types, schemas, mappings, ETL logic |
| **Business Metadata**     | Defines business terms, KPIs, rules, data owners                     |
| **Operational Metadata**  | Tracks ETL process info like job status, data loads, execution times |
| **Process Metadata**      | Describes flow of data through the pipeline                          |
| **Data Lineage Metadata** | Shows origin, movement, and transformation of data                   |
| **Change Metadata**       | Tracks changes (versioning) in schema, business logic, or data       |

---

### **4. Technical Metadata – Key Elements**

* Table names and column names
* Data types, lengths, precision
* Primary and foreign keys
* Indexes, constraints
* ETL transformations and mappings

---

### **5. Business Metadata – Key Elements**

* Definitions of KPIs and metrics
* Business rules and descriptions
* Ownership and stewardship
* Data quality rules
* Usage guidelines and purpose

---

### **6. Operational Metadata – Key Elements**

* ETL job names and run history
* Source-to-target mapping status
* Load timestamps
* Number of rows extracted, transformed, loaded
* Error and log tracking

---

### **7. Metadata Management**

| Activity                | Description                                         |
| ----------------------- | --------------------------------------------------- |
| **Metadata Repository** | Centralized store for all metadata types            |
| **Cataloging**          | Classify and index metadata for discovery           |
| **Lineage Tracking**    | Trace data origin and transformations               |
| **Impact Analysis**     | Assess downstream effects of data or schema changes |
| **Versioning**          | Track changes to metadata over time                 |
| **Governance**          | Apply rules, ownership, and responsibilities        |

---

### **8. Metadata Standards**

| Standard          | Description                                            |
| ----------------- | ------------------------------------------------------ |
| **ISO/IEC 11179** | Standard for metadata registries                       |
| **Dublin Core**   | Standard for descriptive metadata                      |
| **CDISC, HL7**    | Metadata standards for healthcare data                 |
| **OMG CWM**       | Common Warehouse Metamodel (for tool interoperability) |

---

### **9. Metadata Tools**

| Category                 | Examples                                          |
| ------------------------ | ------------------------------------------------- |
| **ETL Metadata Tools**   | Informatica Metadata Manager, Talend, SSIS        |
| **Data Catalogs**        | Apache Atlas, Alation, Collibra, Amundsen         |
| **BI Tools Integration** | Tableau, Power BI, Looker (for semantic metadata) |

---

### **10. Use Cases of Metadata**

* **Data discovery and self-service BI**
* **Impact analysis before schema changes**
* **Data lineage visualization**
* **Compliance and auditing**
* **ETL debugging and optimization**
* **Semantic layer for reporting tools**

---
