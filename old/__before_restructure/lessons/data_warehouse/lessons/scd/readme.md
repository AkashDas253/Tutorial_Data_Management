## **Slowly Changing Dimensions (SCD)**

---

### **1. What is SCD?**

**Slowly Changing Dimensions (SCD)** refer to **dimension attributes** that **change over time** and must be tracked in a data warehouse for **historical accuracy** and **auditing**.

---

### **2. Why SCD is Important**

* Maintains historical context for reports
* Supports **time-based analysis** (e.g., customer moved to new city)
* Enables **data consistency** with business reality

---

### **3. SCD Types**

| Type | Name                      | Description                                       | Data Handling Approach                     |
| ---- | ------------------------- | ------------------------------------------------- | ------------------------------------------ |
| 0    | Fixed Dimension           | No changes allowed once entered                   | Ignore changes                             |
| 1    | Overwrite                 | Update the existing record; no history            | Replace old value                          |
| 2    | Historical Row Versioning | Keep history by adding a new row for every change | Use surrogate key + effective dates        |
| 3    | Previous Value Tracking   | Add new columns to store previous values          | Limited history (e.g., current & previous) |
| 4    | Historical Table          | Use a separate table to track all changes         | Maintain history in an auxiliary table     |
| 6    | Hybrid (1+2+3)            | Combines Type 1, 2, and 3 in the same design      | New row + overwrites + extra columns       |

---

### **4. SCD Type 1 – Overwrite**

| Before       | After Update  |
| ------------ | ------------- |
| City = Delhi | City = Mumbai |

* **No history is kept**
* Simple to implement
* Used when change is not important to track

---

### **5. SCD Type 2 – Historical Tracking**

| Surrogate Key | Customer ID | City   | Start Date | End Date   | Is Current |
| ------------- | ----------- | ------ | ---------- | ---------- | ---------- |
| 1001          | C001        | Delhi  | 2018-01-01 | 2020-06-30 | N          |
| 1002          | C001        | Mumbai | 2020-07-01 | NULL       | Y          |

* **New row** added for every change
* **Effective dates** track period
* Supports **historical analysis**
* **ETL logic** must check for changes and version accordingly

---

### **6. SCD Type 3 – Limited History**

| Customer ID | Current City | Previous City |
| ----------- | ------------ | ------------- |
| C001        | Mumbai       | Delhi         |

* Only **one historical value** stored
* Cannot support full historical reporting
* Easy to implement but limited in use

---

### **7. SCD Type 4 – Historical Table**

* Main dimension has **latest values**
* Separate **history table** stores full changes

**Example:**

* `Customer_Dimension`: stores current city
* `Customer_History`: logs all historical changes

---

### **8. SCD Type 6 – Hybrid**

Combines:

* **Type 1**: overwrite certain attributes
* **Type 2**: row versioning for others
* **Type 3**: add columns for recent values

**Used when:**

* Some attributes need **full history**
* Some need **limited change**
* Some are just **updated**

---

### **9. Choosing SCD Type – When to Use What**

| Situation                              | Use SCD Type |
| -------------------------------------- | ------------ |
| No change allowed                      | Type 0       |
| Change is minor and history irrelevant | Type 1       |
| Need complete history                  | Type 2       |
| Need only recent change                | Type 3       |
| Need both current and full history     | Type 4       |
| Need combination of all behaviors      | Type 6       |

---

### **10. Key SCD Columns**

| Column         | Purpose                             |
| -------------- | ----------------------------------- |
| Surrogate Key  | Unique internal ID for each version |
| Effective Date | When the row became valid           |
| Expiry Date    | When the row stopped being valid    |
| Current Flag   | Boolean to indicate current record  |
| Version Number | Optional for version tracking       |

---
