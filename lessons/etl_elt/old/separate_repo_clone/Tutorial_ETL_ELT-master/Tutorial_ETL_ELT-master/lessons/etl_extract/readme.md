## **Extract Phase – ETL Process**

The **Extract** phase is the first step in the ETL process. It involves retrieving structured, semi-structured, or unstructured data from multiple source systems and moving it into a staging area for transformation.

---

### **Objectives**

* Collect relevant data from all identified sources
* Ensure completeness, accuracy, and consistency
* Minimize the impact on source systems during extraction

---

### **Source Systems**

* **Databases**: MySQL, Oracle, PostgreSQL, MongoDB, SQL Server
* **Flat Files**: CSV, Excel, JSON, XML, TXT
* **Web Services & APIs**: REST, SOAP
* **ERP/CRM systems**: Salesforce, SAP, Microsoft Dynamics
* **Cloud Storage**: AWS S3, Azure Blob Storage, Google Cloud Storage
* **Message Queues**: Kafka, RabbitMQ

---

### **Extraction Types**

| Type                          | Description                                                                |
| ----------------------------- | -------------------------------------------------------------------------- |
| **Full Extraction**           | All data from the source is extracted every time                           |
| **Incremental Extraction**    | Only new or changed records since the last extraction are retrieved        |
| **Change Data Capture (CDC)** | Detects and extracts changes using logs or triggers (insert/update/delete) |

---

### **Extraction Modes**

| Mode                    | Description                                                     |
| ----------------------- | --------------------------------------------------------------- |
| **Batch Extraction**    | Data is pulled at scheduled intervals (e.g., daily, hourly)     |
| **Real-time/Streaming** | Data is extracted continuously using events, queues, or streams |
| **On-Demand**           | Triggered manually or by external processes                     |

---

### **Key Techniques**

* **Timestamps**: Track last updated or inserted records
* **Triggers**: Fire on change to capture data
* **Log Mining**: Extract from transaction logs
* **Snapshots**: Take periodic full snapshots and compare
* **API Calls**: Use endpoints to pull paginated or filtered data

---

### **Staging Area**

* A temporary storage location used to hold raw extracted data
* Isolates source systems from transformation logic
* Enables reprocessing without re-extracting

---

### **Key Considerations**

* **Data Volume**: Optimize for performance and bandwidth
* **Latency Requirements**: Align with business needs (batch vs real-time)
* **Data Quality**: Validate extracted data for completeness and corruption
* **Fault Tolerance**: Implement retries, error handling, and logging
* **Security**: Encrypt data in transit and mask sensitive information
* **Source Impact**: Use non-blocking reads or read replicas when possible

---

### **Best Practices**

* Use consistent naming and schema conventions in staging
* Maintain extraction logs for auditing and debugging
* Optimize queries to reduce load on source systems
* Use parallelism to speed up large extractions
* Separate configuration and connection logic from code

---

### **Common Tools Supporting Extraction**

* **Open Source**: Apache Nifi, Airbyte, Singer
* **Commercial**: Informatica, Talend, SSIS, Fivetran
* **Cloud Services**: AWS Glue, Azure Data Factory, GCP Dataflow

---
