## **Data Warehouse Design**

---

### **1. What is Data Warehouse Design?**

Data warehouse design is the structured process of **organizing, modeling, and structuring data** from different sources into a centralized repository to support **efficient reporting, analytics, and decision-making**.

---

### **2. Goals of Design**

* High **performance** and **scalability**
* Ensure **data quality** and **consistency**
* Simplify **user access** and **reporting**
* Support **historical analysis**
* Handle **large volumes** of data efficiently

---

### **3. Design Approaches**

| Approach      | Description                                           | Key Proponent   |
| ------------- | ----------------------------------------------------- | --------------- |
| **Top-down**  | Start with enterprise DW → build data marts           | Bill Inmon      |
| **Bottom-up** | Build data marts first → integrate into enterprise DW | Ralph Kimball   |
| **Hybrid**    | Combine both methods                                  | Modern practice |

---

### **4. Design Process Steps**

| Step                        | Description                                                     |
| --------------------------- | --------------------------------------------------------------- |
| **Requirement Analysis**    | Understand business goals, KPIs, users, and data sources        |
| **Data Modeling**           | Design logical schema using dimensional or ER modeling          |
| **Architecture Definition** | Choose storage layer, tools, and infrastructure (cloud/on-prem) |
| **ETL Design**              | Plan data extraction, transformation, and loading strategy      |
| **Schema Design**           | Choose between Star, Snowflake, Galaxy schemas                  |
| **Aggregation Strategy**    | Define summary tables, cube structures                          |
| **Indexing & Partitioning** | Optimize performance for large queries                          |
| **Security & Governance**   | Define roles, access control, auditing, metadata management     |

---

### **5. Data Modeling Choices**

| Model Type           | Description                                     | Use Case                               |
| -------------------- | ----------------------------------------------- | -------------------------------------- |
| **Star Schema**      | Central fact table with denormalized dimensions | Simple, fast-query models              |
| **Snowflake Schema** | Normalized dimensions                           | Space-efficient, complex relationships |
| **Galaxy Schema**    | Multiple fact tables with shared dimensions     | Shared metrics across domains          |

---

### **6. Granularity**

* **Grain** = Lowest level of detail captured in the fact table
* Must be **clearly defined and consistent**
* Higher granularity → more data, better analysis flexibility

---

### **7. Fact Table Design**

* **Grain definition** (e.g., one row per sale)
* Choose appropriate **measures**
* Define **foreign keys** to dimension tables
* Use **surrogate keys** if needed

---

### **8. Dimension Table Design**

* Rich in descriptive attributes
* Handle **Slowly Changing Dimensions (SCD)**
* Use **hierarchies** for drill-down (e.g., Country → State → City)
* Conform dimensions for consistency across fact tables

---

### **9. Performance Optimization**

| Technique              | Purpose                               |
| ---------------------- | ------------------------------------- |
| **Indexes**            | Speed up query access                 |
| **Partitioning**       | Divide large tables for manageability |
| **Materialized Views** | Store precomputed summaries           |
| **Aggregates**         | Speed up common grouped queries       |
| **Columnar Storage**   | Optimize analytics workloads          |

---

### **10. Data Marts in Design**

| Type            | Description                                 |
| --------------- | ------------------------------------------- |
| **Dependent**   | Sourced from central DW                     |
| **Independent** | Built from source systems directly          |
| **Logical**     | Virtual views or layers in a centralized DW |

---

### **11. Metadata Design**

| Metadata Type            | Purpose                                   |
| ------------------------ | ----------------------------------------- |
| **Business Metadata**    | Definitions, KPI meanings                 |
| **Technical Metadata**   | Schema, datatype, transformation logic    |
| **Operational Metadata** | ETL job history, load times, job failures |

---

### **12. Security and Access Control**

* Row-level and column-level security
* Role-based access
* Auditing and data lineage
* Encryption (at-rest and in-transit)

---

### **13. Modern Design Considerations**

* **Cloud-native** warehouses (Snowflake, BigQuery, Redshift)
* **Data Lake Integration**
* **Real-time ingestion** (Lambda architecture)
* **ELT pipelines** (vs traditional ETL)
* **Data Vault Modeling** for agile development

---
