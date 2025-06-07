## **ETL Load**

---

### **1. What is Load?**

**Load** is the final phase of the ETL process where the **transformed data** is **written into the target system**, usually a **data warehouse, data mart, or data lake**.

---

### **2. Purpose of Load**

* Persist the processed data for **querying and reporting**
* Ensure data integrity and consistency in the target
* Support historical and real-time analytical needs

---

### **3. Types of Load**

| Load Type            | Description                                                     | Use Case                                       |
| -------------------- | --------------------------------------------------------------- | ---------------------------------------------- |
| **Full Load**        | Overwrites entire target data with fresh data                   | Initial load or complete refresh               |
| **Incremental Load** | Loads only new or changed records since last load               | Efficient for large datasets, keeps DW updated |
| **Initial Load**     | First-time bulk load of all historical data                     | Setting up DW for the first time               |
| **Delta Load**       | Loads only delta changes detected via Change Data Capture (CDC) | Real-time or near real-time updates            |
| **Batch Load**       | Loads data in scheduled batches                                 | Most common for periodic updates               |
| **Real-time Load**   | Streams data continuously as it arrives                         | Real-time dashboards, monitoring systems       |

---

### **4. Load Techniques**

| Technique          | Description                                      | Pros                        | Cons                       |
| ------------------ | ------------------------------------------------ | --------------------------- | -------------------------- |
| **Insert**         | Append new records                               | Simple                      | May cause duplicates       |
| **Update**         | Modify existing records                          | Keeps data current          | Complex for large datasets |
| **Upsert (Merge)** | Insert new or update existing records            | Efficient for incremental   | Requires key management    |
| **Bulk Load**      | Load large volumes at once using bulk APIs/tools | Fast                        | Requires downtime/locking  |
| **Partition Load** | Load data into specific partitions               | Optimizes query performance | Complex partitioning logic |

---

### **5. Load Validation & Integrity**

* Check **record counts** to ensure expected load
* Validate **constraints and keys** (primary, foreign keys)
* Enforce **data quality rules** post-load
* Maintain **audit logs** for data traceability
* Handle **error records** via reject files or alerts

---

### **6. Performance Considerations**

* Use **batch commits** to optimize transaction size
* Disable **indexes and constraints** during bulk load (rebuild after)
* Load in **parallel** when supported by target system
* Monitor load times and tune accordingly

---

### **7. Load in Data Warehousing Context**

* Load **fact tables** and **dimension tables** as per the schema
* Handle **Slowly Changing Dimensions (SCD)** correctly
* Maintain **historical data** for trend and time-series analysis
* Use **surrogate keys** consistently during load

---

### **8. Tools & Technologies for Loading**

| Category            | Examples                                            |
| ------------------- | --------------------------------------------------- |
| ETL Tools           | Informatica, Talend, Microsoft SSIS                 |
| Bulk Load Utilities | SQL\*Loader (Oracle), BCP (SQL Server)              |
| Cloud Services      | AWS Glue, Azure Data Factory, Google Cloud Dataflow |

---

### **9. Common Load Errors**

| Error Type            | Description                                 |
| --------------------- | ------------------------------------------- |
| Constraint Violations | Duplicate keys, foreign key mismatches      |
| Data Type Mismatch    | Source data incompatible with target schema |
| Disk/Storage Issues   | Insufficient space or permissions           |
| Network Failures      | Interruptions during load                   |

---

### **10. Summary**

Loading is the **final critical step** that ensures transformed data is **persisted correctly and efficiently** in the target repository to support downstream analytics, reporting, and decision making.

---
