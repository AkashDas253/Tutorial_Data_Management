## **ETL Extraction**

---

### **1. What is Extraction?**

**Extraction** is the first phase of the ETL process where data is **collected** from various **source systems** and brought into the staging area for further processing.

---

### **2. Purpose of Extraction**

* To gather relevant data from heterogeneous sources
* To capture data in a way that minimally impacts source system performance
* To ensure data completeness and accuracy for transformation

---

### **3. Types of Extraction Methods**

| Method                         | Description                                                     | Use Case / Notes                                |
| ------------------------------ | --------------------------------------------------------------- | ----------------------------------------------- |
| **Full Extraction**            | Extracts the entire dataset every time                          | Simple, but inefficient for large data          |
| **Incremental Extraction**     | Extracts only new or changed data since last extraction         | Efficient for large, frequently changing data   |
| **Log-Based Extraction**       | Uses transaction logs (e.g., database logs) to identify changes | Minimizes impact on source; requires DB support |
| **Trigger-Based Extraction**   | Uses database triggers to capture changes in real-time          | Real-time data capture; complex to implement    |
| **Timestamp-Based Extraction** | Extracts rows updated after a certain timestamp                 | Common for incremental extraction               |

---

### **4. Common Source Systems**

| Source Type          | Examples                              |
| -------------------- | ------------------------------------- |
| Relational Databases | Oracle, SQL Server, MySQL, PostgreSQL |
| Flat Files           | CSV, TXT, Excel sheets                |
| APIs / Web Services  | RESTful, SOAP APIs                    |
| NoSQL Databases      | MongoDB, Cassandra                    |
| Cloud Storage        | AWS S3, Azure Blob Storage            |
| Legacy Systems       | Mainframes, ERP systems               |

---

### **5. Extraction Techniques**

| Technique                     | Description                                | Pros                            | Cons                             |
| ----------------------------- | ------------------------------------------ | ------------------------------- | -------------------------------- |
| **Bulk Extraction**           | Extract large volumes of data at once      | Simple to implement             | Heavy load on source system      |
| **Change Data Capture (CDC)** | Extract only changes since last extraction | Efficient, less source impact   | Complex to setup, requires logs  |
| **Query-Based**               | Use SQL queries to extract data            | Flexible and selective          | May impact source DB performance |
| **Snapshot Extraction**       | Capture state of data at a point in time   | Useful for historical snapshots | Large volume of data             |

---

### **6. Extraction Challenges**

| Challenge            | Description                                           |
| -------------------- | ----------------------------------------------------- |
| Data Volume          | Large data size can slow extraction                   |
| Source System Impact | Extraction should minimize load on production systems |
| Data Consistency     | Extracted data must be consistent and accurate        |
| Connectivity Issues  | Network failures or downtime affect extraction        |
| Schema Changes       | Source schema changes require adjustments             |

---

### **7. Best Practices for Extraction**

* Use **incremental extraction** when possible to reduce load
* Schedule extraction during **off-peak hours** if full extraction is needed
* Monitor source system performance and extraction duration
* Validate data completeness after extraction
* Handle **schema changes** proactively via metadata management
* Use **error handling and logging** to track extraction failures

---

### **8. Extraction Metadata**

* Source system name and type
* Extraction timestamp
* Extraction method used
* Row counts and error counts
* Last extraction date for incremental loads

---

### **9. Tools & Technologies for Extraction**

| Category    | Examples                               |
| ----------- | -------------------------------------- |
| ETL Tools   | Informatica, Talend, SSIS, Apache NiFi |
| CDC Tools   | Oracle GoldenGate, Debezium, Attunity  |
| API Clients | Postman, custom scripts (Python, Java) |

---

### **10. Summary**

Extraction is a **critical step** that sets the foundation for data quality and timeliness in ETL. Choosing the right extraction method and monitoring its execution is key to a successful ETL pipeline.

---
