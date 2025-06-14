## **Types of Fact Tables**

---

### **1. Overview**

Fact tables store the measurable, quantitative data related to business processes. They differ based on how data is collected, aggregated, and the business scenarios they represent.

---

### **2. Types of Fact Tables**

| Type                                 | Description                                                                                   | Grain/Detail Level                                 | Example                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------- | -------------------------------------------------- | --------------------------------------------------------------- |
| **Transactional Fact Table**         | Captures data about individual, atomic business events (most detailed level).                 | Fine-grained; one row per transaction or event     | Each sales order line, each payment                             |
| **Snapshot Fact Table**              | Stores aggregated data representing the state of a process at a specific point in time.       | Periodic (daily, monthly) or event-driven snapshot | Monthly account balance, daily inventory levels                 |
| **Accumulating Snapshot Fact Table** | Tracks the progress of a process with multiple milestones, updated as the process advances.   | One row per process instance; updates over time    | Order fulfillment tracking (order placed → shipped → delivered) |
| **Factless Fact Table**              | Contains only foreign keys to dimensions, no numeric measures; captures events or conditions. | Event tracking or coverage tables                  | Student attendance, product promotion participation             |

---

### **3. Detailed Description**

#### Transactional Fact Table

* Records every individual transaction or event.
* Highest granularity (most detailed).
* Commonly used for detailed analysis and drill-down reports.
* Example: A record for each item sold in a store.

#### Snapshot Fact Table

* Captures the state of a process or condition at a regular interval or event.
* Useful for trending and historical comparisons.
* Can be periodic (e.g., daily, monthly snapshots) or triggered by events.
* Example: Bank account balances at the end of each month.

#### Accumulating Snapshot Fact Table

* Tracks a process with several stages or milestones.
* Contains one row per process instance.
* Updates existing rows as process milestones are reached.
* Useful for workflow or lifecycle analysis.
* Example: Order processing lifecycle from order creation to shipment.

#### Factless Fact Table

* Has no numeric facts; only dimension keys.
* Used to track the occurrence or absence of events.
* Enables analysis of coverage or participation.
* Example: Tracking student attendance in classes or employee training sessions.

---

### **4. Summary Table**

| Fact Table Type       | Grain                            | Data Stored                  | Use Case                           |
| --------------------- | -------------------------------- | ---------------------------- | ---------------------------------- |
| Transactional         | Per individual event/transaction | Measures and dimension keys  | Sales transactions, invoices       |
| Snapshot              | At a time point or interval      | Aggregated measures          | Account balances, inventory levels |
| Accumulating Snapshot | Per process instance             | Milestone dates and measures | Order fulfillment stages           |
| Factless              | Per event occurrence             | Only dimension keys          | Attendance, promotions             |

---

### **5. Considerations**

* Choose fact table type based on **business requirements** and **analysis needs**.
* Transactional facts enable detailed drill-down.
* Snapshot facts enable trend and state analysis.
* Accumulating snapshot facts support lifecycle tracking.
* Factless facts support event coverage and occurrence analysis.

---
