## **Fact Table**

---

### **1. Definition**

A **Fact Table** is the central table in a star or snowflake schema of a data warehouse. It stores **quantitative data (measures)** for analysis and contains **foreign keys** referencing associated **dimension tables**. It records **business process events or transactions**.

---

### **2. Purpose**

* Stores business process **metrics** (e.g., sales amount, units sold)
* Enables **OLAP operations** such as aggregation, slicing, and dicing
* Acts as the core for **schema joins** and analytical queries

---

### **3. Key Characteristics**

| Characteristic                | Description                                            |
| ----------------------------- | ------------------------------------------------------ |
| **Contains measures**         | Numeric values for aggregation (SUM, AVG, etc.)        |
| **Contains foreign keys**     | References to dimension tables                         |
| **Large volume**              | Can have millions or billions of rows                  |
| **High granularity**          | Level of detail determined by the business need        |
| **Additive or semi-additive** | Measures can be aggregated over some or all dimensions |
| **Immutable**                 | Usually append-only; facts rarely updated after insert |

---

### **4. Components of a Fact Table**

| Component            | Description                                                                        |
| -------------------- | ---------------------------------------------------------------------------------- |
| **Fact/Measure**     | Numeric data such as revenue, cost, quantity                                       |
| **Foreign Keys**     | Link to dimension tables (e.g., product\_id, time\_id)                             |
| **Surrogate Key**    | Optional primary key unique to each fact row                                       |
| **Degenerate Key**   | Transactional identifiers stored directly in the fact table (e.g., invoice number) |
| **Metadata Columns** | Optional columns for audit or tracking (e.g., load date)                           |

---

### **5. Types of Facts**

| Type              | Description                                    | Example                     |
| ----------------- | ---------------------------------------------- | --------------------------- |
| **Additive**      | Can be summed across all dimensions            | Sales amount, quantity sold |
| **Semi-additive** | Can be summed over some dimensions but not all | Account balance over time   |
| **Non-additive**  | Cannot be summed across any dimension          | Ratios, percentages         |
| **Derived**       | Calculated from other measures                 | Profit = revenue - cost     |

---

### **6. Types of Fact Tables**

| Type                   | Description                                        | Example                 |
| ---------------------- | -------------------------------------------------- | ----------------------- |
| **Transactional Fact** | Records individual business events or transactions | Every sale              |
| **Snapshot Fact**      | Captures data snapshots at regular intervals       | Monthly account balance |
| **Accumulating Fact**  | Tracks progress of a process with milestone dates  | Order lifecycle stages  |

---

### **7. Grain of the Fact Table**

* **Definition:** The level of detail stored in each record (e.g., per transaction, per customer per day)
* **Examples:**

  * Per transaction (fine granularity)
  * Per product per month (coarser granularity)
* Must be **defined clearly and consistently** before designing facts and dimensions.

---

### **8. Best Practices**

* Define **grain** before identifying facts and dimensions.
* Use **surrogate keys** for foreign key references for performance and history tracking.
* Keep **measure columns atomic** and store derived measures separately if needed.
* Normalize or denormalize dimension tables based on schema design (star vs snowflake).
* Include **audit metadata** such as load date, source system, and versioning for traceability.
* Consider partitioning large fact tables for performance and manage growth with archiving or summarization.

---

### **9. Example Fact Table**

| Sale\_ID | Date\_Key | Customer\_Key | Product\_Key | Store\_Key | Quantity | Sales\_Amount | Invoice\_Number (Degenerate Key) |
| -------- | --------- | ------------- | ------------ | ---------- | -------- | ------------- | -------------------------------- |
| 1001     | 20240601  | 200           | 501          | 10         | 3        | 150.00        | INV12345                         |

---

### **10. Benefits**

* Acts as the **central repository** for measurable business data.
* Supports **fast aggregations** and **trend analysis**.
* Enables **multi-dimensional analysis** through linked dimensions.

---

### **11. Challenges**

* Managing **large data volume** and growth over time.
* Choosing the **right granularity** for use cases.
* Handling **semi-additive and non-additive measures** correctly.
* Ensuring **data quality** and consistency during ETL.

---
