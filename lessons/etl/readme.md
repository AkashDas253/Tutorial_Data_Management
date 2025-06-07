## **ETL (Extract, Transform, Load)**

---

### **1. What is ETL?**

**ETL** is a **data integration process** that **Extracts** data from source systems, **Transforms** it into a suitable format, and **Loads** it into a **data warehouse** or other target system.

---

### **2. ETL Flow**

```
[Source Systems] → [Staging Area] → [Transformation Engine] → [Data Warehouse]
```

---

### **3. ETL Stages**

| Stage         | Description                                                              |
| ------------- | ------------------------------------------------------------------------ |
| **Extract**   | Collect data from multiple, heterogeneous sources (e.g., DB, API, files) |
| **Transform** | Clean, standardize, and apply business rules to make data consistent     |
| **Load**      | Move data into the target system (e.g., data warehouse)                  |

---

### **4. Extract Phase**

| Aspect                  | Description                                                    |
| ----------------------- | -------------------------------------------------------------- |
| **Source Types**        | Relational DBs, CSV files, APIs, cloud services, NoSQL, logs   |
| **Types of Extraction** | Full (entire data), Incremental (changes only), Snapshot-based |
| **Challenges**          | Connectivity, performance, handling change data capture (CDC)  |

---

### **5. Transform Phase**

| Transformation Task          | Description                                                    |
| ---------------------------- | -------------------------------------------------------------- |
| **Data Cleansing**           | Remove duplicates, nulls, outliers                             |
| **Data Mapping**             | Align fields between source and target                         |
| **Data Standardization**     | Convert formats (e.g., dates, currency, units)                 |
| **Business Rules**           | Apply logic like revenue = quantity × unit price               |
| **Derivation**               | Create new columns from existing data                          |
| **Surrogate Key Generation** | Generate IDs for dimensions/facts                              |
| **SCD Handling**             | Track changes in dimension values (SCD 1/2/3/etc.)             |
| **Data Validation**          | Ensure data quality (e.g., constraints, referential integrity) |

---

### **6. Load Phase**

| Type                 | Description                                                |
| -------------------- | ---------------------------------------------------------- |
| **Full Load**        | Overwrites existing data entirely                          |
| **Incremental Load** | Only loads new or changed data                             |
| **Initial Load**     | First-time historical bulk load                            |
| **Delta Load**       | Only changed records since last load (change data capture) |
| **Real-time Load**   | Streams data into the target as events occur               |

---

### **7. ETL Architecture Components**

| Component                | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| **Source Systems**       | Where data originates from                                |
| **Staging Area**         | Temporary storage for raw extracted data                  |
| **Transformation Layer** | Processes data according to business logic                |
| **Loading Layer**        | Writes processed data to the final target (DW, Data Lake) |
| **Metadata Repository**  | Stores ETL rules, mappings, logs                          |
| **ETL Scheduler**        | Manages and triggers ETL jobs on schedule or events       |

---

### **8. ETL vs ELT**

| Feature             | ETL (Traditional)                        | ELT (Modern)                               |
| ------------------- | ---------------------------------------- | ------------------------------------------ |
| **Order**           | Transform before loading                 | Load before transforming                   |
| **Processing Tool** | ETL tool handles transformation          | Target system (e.g., cloud DW) does it     |
| **When to Use**     | When target has limited processing power | When target has high processing capability |
| **Examples**        | Informatica, Talend                      | BigQuery, Snowflake, Redshift              |

---

### **9. Popular ETL Tools**

| Type            | Tools                                                              |
| --------------- | ------------------------------------------------------------------ |
| **Commercial**  | Informatica PowerCenter, IBM DataStage, Microsoft SSIS             |
| **Open Source** | Apache NiFi, Talend Open Studio, Pentaho Data Integration (Kettle) |
| **Cloud-based** | AWS Glue, Azure Data Factory, Google Cloud Dataflow                |

---

### **10. Key Challenges in ETL**

| Challenge               | Description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| **Scalability**         | Large data volumes may slow ETL                              |
| **Data Quality**        | Inconsistent or incomplete data needs cleansing              |
| **Latency**             | Batch ETL introduces delay in reporting                      |
| **Error Handling**      | Failures during load/transform must be detected and resolved |
| **Change Data Capture** | Identifying updates from source systems efficiently          |

---

### **11. Benefits of ETL**

* Integrates diverse data sources
* Improves data quality and consistency
* Enables historical data analysis
* Prepares data for BI and reporting

---
