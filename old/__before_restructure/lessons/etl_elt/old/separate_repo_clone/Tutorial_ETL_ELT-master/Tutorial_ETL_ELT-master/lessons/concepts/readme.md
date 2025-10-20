## **ETL and ELT Concepts and Subconcepts**

### **1. Data Integration**

* Data sources

  * Relational databases
  * NoSQL databases
  * Flat files
  * APIs / Web services
  * Cloud sources
* Data targets

  * Data warehouses
  * Data lakes
  * Operational data stores

---

### **2. ETL Process**

#### **Extract**

* Full extraction
* Incremental extraction
* Change Data Capture (CDC)
* Source system connection
* Data staging

#### **Transform**

* Data cleaning

  * Removing duplicates
  * Handling nulls
  * Correcting data types
* Data standardization
* Data deduplication
* Data enrichment
* Business rule application
* Data validation
* Data mapping
* Join and merge
* Aggregation
* Filtering
* Sorting

#### **Load**

* Initial load
* Incremental load
* Batch load
* Real-time/Streaming load
* Load strategies

  * Insert only
  * Upsert (Insert + Update)
  * Slowly Changing Dimensions (SCD)

    * Type 0, 1, 2, 3, 6

---

### **3. ELT Process**

#### **Extract**

* Similar to ETL extract step

#### **Load**

* Raw data pushed directly into data warehouse or data lake
* Data stored in staging or raw schema

#### **Transform**

* Performed within the target system
* SQL-based transformations
* In-database transformations
* Leveraging MPP (Massively Parallel Processing) engines

---

### **4. Transformation Techniques**

* Lookup transformations
* Join transformations
* Expression transformations
* Union transformations
* Pivot/Unpivot
* Normalization / Denormalization
* Surrogate key generation

---

### **5. Orchestration and Scheduling**

* Job dependencies
* Workflow design
* Job scheduling
* Retry and alerting
* Parallel and sequential execution

---

### **6. Performance Optimization**

* Partitioning
* Pushdown optimization (ETL)
* ELT in-database processing
* Pipeline parallelism
* Memory management
* Indexing and materialized views (for ELT)

---

### **7. Error Handling and Logging**

* Error detection and isolation
* Logging and audit trails
* Retry mechanisms
* Data reconciliation
* Alerting and notifications

---

### **8. Data Governance and Quality**

* Data profiling
* Data quality metrics

  * Accuracy, completeness, consistency, validity, timeliness
* Metadata management
* Master data management (MDM)
* Data lineage
* Compliance and audit

---

### **9. Tools and Technologies**

* ETL Tools

  * Apache Nifi
  * Talend
  * Informatica PowerCenter
  * Microsoft SSIS
  * IBM DataStage
* ELT Tools

  * dbt (Data Build Tool)
  * Azure Data Factory
  * Snowflake ELT
  * Google BigQuery
  * AWS Glue
* Hybrid Tools

  * Apache Airflow
  * Apache Beam
  * Matillion

---

### **10. Storage and Processing Targets**

* Data warehouses

  * Snowflake, Redshift, BigQuery, Azure Synapse
* Data lakes

  * Amazon S3, Azure Data Lake, Hadoop HDFS
* Lakehouses

  * Databricks, Delta Lake

---

### **11. Real-time and Streaming ETL/ELT**

* Stream ingestion tools

  * Apache Kafka
  * Apache Flink
  * Amazon Kinesis
* Stream processing

  * Micro-batch processing
  * Event-driven architecture

---

### **12. Cloud vs On-Premise**

* Scalability
* Maintenance overhead
* Cost management
* Deployment strategies

---

### **13. Security and Compliance**

* Data encryption
* Access control and IAM
* GDPR, HIPAA, CCPA
* Secure data masking

---
