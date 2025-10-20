## **ETL Extraction**

---

### **What is Extraction?**

**Extraction** is the **first step** in the ETL process where **data is retrieved** from various **source systems** (structured, semi-structured, or unstructured) and moved into a **staging area** for transformation.

---

### **2. Purpose / Objectives of Extraction**

* Gather relevant data from all identified sources
* Minimize the impact on source systems during extraction
* Ensure **completeness, accuracy, and consistency**
* Set a strong foundation for transformation and loading

---

### **Types of Extraction**

| Type                          | Description                                                                |
| ----------------------------- | -------------------------------------------------------------------------- |
| **Full Extraction**           | All data from the source is extracted every time                           |
| **Incremental Extraction**    | Only new or changed records since the last extraction are retrieved        |
| **Change Data Capture (CDC)** | Detects and extracts changes using logs or triggers (insert/update/delete) |
| **Timestamp-Based**           | Extract rows updated after a certain timestamp                             |
| **Trigger-Based**             | Use triggers to track and extract changes in real-time                     |
| **Log-Based**                 | Use transaction logs for capturing changes                                 |

---

### **Extraction Modes**

| Mode                    | Description                                                |
| ----------------------- | ---------------------------------------------------------- |
| **Batch Extraction**    | Data pulled at scheduled intervals (e.g., daily, hourly)   |
| **Real-time/Streaming** | Data extracted continuously via events, streams, or queues |
| **On-Demand**           | Triggered manually or by external processes                |

---

### **Extraction Techniques**

| Technique                     | Description                              | Pros                            | Cons                        |
| ----------------------------- | ---------------------------------------- | ------------------------------- | --------------------------- |
| **Bulk Extraction**           | Extract large volumes at once            | Simple implementation           | Heavy load on source        |
| **CDC (Change Data Capture)** | Capture incremental changes              | Low latency, less impact        | Requires setup & log access |
| **Query-Based**               | Extract via custom SQL queries           | Flexible, selective             | May impact DB performance   |
| **Snapshot Extraction**       | Capture state of data at a point in time | Useful for auditing/historicals | High volume if frequent     |

---

### **Common Source Systems**

| Source Type             | Examples                                        |
| ----------------------- | ----------------------------------------------- |
| **Databases**           | Oracle, SQL Server, MySQL, PostgreSQL, MongoDB  |
| **Flat Files**          | CSV, Excel, JSON, XML, TXT                      |
| **Web Services / APIs** | RESTful APIs, SOAP                              |
| **ERP/CRM Systems**     | Salesforce, SAP, Microsoft Dynamics             |
| **Cloud Storage**       | AWS S3, Azure Blob, Google Cloud Storage        |
| **Message Queues**      | Apache Kafka, RabbitMQ                          |
| **Legacy Systems**      | Mainframes, file-based or proprietary databases |

---

### **Staging Area**

* **Temporary storage** for raw extracted data
* **Isolates** extraction from transformation and loading
* Allows **reprocessing** without repeated extraction
* May reside in **file systems, databases, or cloud buckets**

---

### **Extraction Metadata to Track**

* Source system name and type
* Timestamp of extraction
* Method used (full, incremental, CDC, etc.)
* Record counts (success/failure)
* Last successful extraction timestamp

---

### **Key Considerations**

| Consideration        | Description                                                |
| -------------------- | ---------------------------------------------------------- |
| **Data Volume**      | Optimize bandwidth and load; consider partitioning         |
| **Latency Needs**    | Choose batch or real-time based on business needs          |
| **Source Impact**    | Avoid blocking reads; use replicas or non-peak hours       |
| **Fault Tolerance**  | Implement retry mechanisms and error logging               |
| **Security**         | Encrypt in transit; mask sensitive fields                  |
| **Data Quality**     | Validate extracted data; check completeness and corruption |
| **Schema Evolution** | Adjust to changes in source schema proactively             |

---

### **Best Practices**

* Prefer **incremental extraction** for large and dynamic sources
* Schedule full loads during **non-peak hours**
* Monitor **performance metrics** and source impact
* Use **parallelism** and **batching** for large data sets
* Maintain **audit logs** and **error logs**
* Separate **connection/config logic** from extraction logic
* Use **metadata-driven** extraction where possible

---

### **Common Tools Supporting Extraction**

| Type            | Tools / Examples                            |
| --------------- | ------------------------------------------- |
| **ETL Tools**   | Talend, Informatica, SSIS, Apache Nifi      |
| **CDC Tools**   | Oracle GoldenGate, Debezium, Qlik Replicate |
| **API Clients** | Postman, Python Requests, Java, etc.        |
| **Cloud ETL**   | AWS Glue, Azure Data Factory, GCP Dataflow  |
| **Open Source** | Airbyte, Singer                             |

---

### **Summary**

The **Extract phase** is crucial for ensuring reliable and timely data movement from **diverse source systems** into the pipeline. **Efficiency, consistency, and minimal source system disruption** are the primary goals. Choosing the right extraction method, tracking metadata, and handling errors effectively leads to a robust and scalable ETL process.

---
