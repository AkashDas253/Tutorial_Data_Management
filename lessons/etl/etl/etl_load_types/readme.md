## **Load Types in ETL/ELT**

---

### **1. Introduction to Loading**

Loading is the final ETL step where transformed (or raw, in ELT) data is moved into the target system such as a data warehouse, data mart, or data lake.

---

### **2. Types of Loading**

| Load Type                      | Description                                                                                               | Use Case / Pros                                      | Cons / Challenges                                        |
| ------------------------------ | --------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- | -------------------------------------------------------- |
| **Full Load**                  | Loads the entire dataset fresh into the target system, often by truncating and reloading the target table | Simple and reliable for small datasets               | Time-consuming and resource-heavy; overwrites all data   |
| **Incremental Load**           | Loads only new or changed data since the last load, often using timestamps or change tracking             | Efficient for large datasets; minimizes load         | Complex logic to detect changes; risk of missing updates |
| **Batch Load**                 | Loads data in batches at scheduled intervals (e.g., hourly, daily)                                        | Balances load and data freshness                     | Latency in data availability                             |
| **Real-Time / Streaming Load** | Loads data continuously or near real-time as it arrives                                                   | Supports real-time analytics                         | Complex infrastructure; high resource use                |
| **Trickle Load**               | Similar to real-time but smaller, frequent loads to keep data near up-to-date                             | Lower latency than batch, easier than full streaming | Still requires careful coordination                      |
| **Upsert Load**                | Combines insert and update operations: inserts new records, updates existing ones                         | Maintains data integrity and history                 | Complex to implement; performance overhead               |
| **Overwrite Load**             | Completely replaces existing data in the target table with new data                                       | Ensures data consistency                             | Data downtime; large resource use                        |
| **Append Load**                | Adds new records to existing data without modifying existing rows                                         | Simple and fast                                      | Can cause duplicates if not managed                      |
| **Parallel Load**              | Splits loading into multiple parallel processes to improve speed                                          | Speeds up load process                               | Requires careful handling of concurrency                 |
| **Bulk Load**                  | Uses database-specific bulk utilities to load large volumes efficiently                                   | Fast and efficient for big data                      | Limited control over logging or error handling           |

---

### **3. Load Type Selection Criteria**

* Data volume and frequency requirements
* Target system capabilities
* Data latency needs (real-time vs batch)
* Data integrity and historical preservation needs
* Complexity and maintenance considerations

---

### **4. Summary Table**

| Load Type        | Key Feature                | Best For                             | Drawbacks                      |
| ---------------- | -------------------------- | ------------------------------------ | ------------------------------ |
| Full Load        | Reload entire dataset      | Small data or initial load           | Time/resource intensive        |
| Incremental Load | Load only changed/new data | Large datasets, efficiency           | Complex change detection logic |
| Batch Load       | Scheduled loads            | Standard periodic updates            | Latency in data                |
| Real-Time Load   | Continuous loading         | Low latency, streaming data          | Complex, high resource use     |
| Trickle Load     | Frequent small loads       | Near real-time needs                 | Coordination complexity        |
| Upsert Load      | Insert + update operations | Data integrity, slowly changing data | Complex implementation         |
| Overwrite Load   | Replace data completely    | Simple data refresh                  | Downtime, resource heavy       |
| Append Load      | Add new records only       | Simple, fast inserts                 | Duplicate risk                 |
| Parallel Load    | Concurrent loading         | Speed up big data loads              | Concurrency handling required  |
| Bulk Load        | Database bulk utilities    | Very large data volumes              | Limited error control          |

---
