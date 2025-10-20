## **Types of Extraction in ETL**

---

### **1. Introduction to Extraction**

Extraction is the first step in ETL/ELT processes where data is collected from source systems. The method chosen affects data freshness, system load, and overall ETL performance.

---

### **2. Types of Extraction**

| Extraction Type               | Description                                                                     | Use Case / Pros                                               | Cons / Challenges                                               |
| ----------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| **Full Extraction**           | Extracts the entire dataset from the source every time.                         | Simple to implement; ensures full data capture                | Time-consuming and resource-intensive; duplicates need handling |
| **Incremental Extraction**    | Extracts only new or changed data since the last extraction                     | Efficient for large datasets; reduces load                    | Requires tracking mechanism; complex logic to identify changes  |
| **Log-Based Extraction**      | Uses database transaction logs (e.g., redo logs, binlogs) to capture changes    | Real-time or near real-time extraction; minimal source impact | Complex setup; depends on DB support and permissions            |
| **Trigger-Based Extraction**  | Database triggers capture changes and store them in staging tables              | Accurate change capture; real-time possible                   | Overhead on source system; triggers can affect performance      |
| **Change Data Capture (CDC)** | Captures data changes using various methods (log-based, timestamp, triggers)    | Efficient, minimizes data volume; real-time or batch          | Complex implementation; depends on source capabilities          |
| **Query-Based Extraction**    | Uses queries with filters or conditions to fetch relevant data                  | Flexible; can be optimized per need                           | Depends on query performance; may impact source system          |
| **API-Based Extraction**      | Extracts data via APIs exposed by source systems                                | Used for SaaS/cloud sources; flexible and standardized        | Rate limits and latency; complexity varies by API               |
| **Snapshot Extraction**       | Periodic snapshots of data state (similar to full extract but at set intervals) | Good for slowly changing data; simple to understand           | Data redundancy; higher storage and processing overhead         |
| **Hybrid Extraction**         | Combination of two or more extraction types (e.g., full plus incremental)       | Balances completeness and efficiency                          | Complexity in design and management                             |

---

### **3. Extraction Type Selection Criteria**

* **Data volume and velocity**
* **Source system capabilities and limitations**
* **Latency requirements (real-time vs batch)**
* **System load impact tolerance**
* **Complexity and maintenance effort**

---

### **4. Summary Table**

| Type                     | Key Feature                    | Best For                       | Drawbacks                      |
| ------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| Full Extraction          | Entire data every time         | Small or simple data sets      | High resource usage            |
| Incremental Extraction   | Only new/changed data          | Large datasets, efficient ETL  | Complex tracking required      |
| Log-Based Extraction     | Uses DB transaction logs       | Real-time, minimal source load | Complex to implement           |
| Trigger-Based Extraction | DB triggers capture changes    | Accurate, near real-time       | Source performance overhead    |
| CDC                      | Various change capture methods | Efficient, scalable            | Complex setup                  |
| Query-Based Extraction   | Custom queries with filters    | Flexible                       | Source performance dependent   |
| API-Based Extraction     | Extracts via APIs              | Cloud/SaaS systems             | Rate limits, latency           |
| Snapshot Extraction      | Periodic full snapshots        | Slowly changing data           | Data duplication, storage cost |
| Hybrid Extraction        | Combined approaches            | Complex environments           | Higher design complexity       |

---
