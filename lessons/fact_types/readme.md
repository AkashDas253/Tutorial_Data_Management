## **Types of Facts**

---

### **1. Overview**

Facts in dimensional modeling are the numeric measurements or metrics stored in fact tables that represent business processes or events. Based on their nature and aggregation behavior, facts are classified into different types.

---

### **2. Types of Facts**

| Type                                 | Description                                                                                        | Aggregation Behavior                             | Example                                 |
| ------------------------------------ | -------------------------------------------------------------------------------------------------- | ------------------------------------------------ | --------------------------------------- |
| **Additive Facts**                   | Facts that can be summed across all dimensions without any restriction.                            | Fully additive over all dimensions               | Sales Amount, Quantity Sold, Total Cost |
| **Semi-Additive Facts**              | Facts that can be aggregated across some dimensions but **not** all, typically not over time.      | Aggregatable across some dimensions but not time | Account Balance, Inventory Level        |
| **Non-Additive Facts**               | Facts that **cannot** be aggregated across any dimension meaningfully.                             | Not additive over any dimension                  | Ratios, Percentages, Averages           |
| **Derived Facts (Calculated Facts)** | Facts computed from other facts or data, often not stored physically but calculated at query time. | Depends on calculation logic                     | Profit (Revenue – Cost), Growth Rate    |

---

### **3. Detailed Explanation**

#### Additive Facts

* Most common fact type.
* Supports straightforward aggregation like SUM.
* Useful for metrics such as revenue, units sold, and total cost.
* Aggregations can be done by time, location, product, etc.

#### Semi-Additive Facts

* Can be summed across some dimensions but not all.
* Commonly, they cannot be summed across the **time** dimension.
* Example: Account balance can be summed across accounts or branches but summing over days would distort the meaning.
* Requires special aggregation functions like LAST, AVG, MAX depending on context.

#### Non-Additive Facts

* Metrics that don’t aggregate meaningfully.
* Examples include percentages (e.g., profit margin), ratios (e.g., conversion rate), or averages.
* Special handling needed in reports to avoid incorrect summation.
* Usually calculated during query time or stored as pre-calculated aggregates.

#### Derived Facts

* Computed from one or more existing facts.
* Example: Profit = Revenue - Cost.
* Can be stored or calculated on the fly.
* Helps reduce data redundancy and storage but may impact query performance if computed frequently.

---

### **4. Summary Table**

| Fact Type            | Aggregatable Over Time | Aggregatable Over Other Dimensions | Example                 | Aggregation Function         |
| -------------------- | ---------------------- | ---------------------------------- | ----------------------- | ---------------------------- |
| Additive             | Yes                    | Yes                                | Sales Amount            | SUM                          |
| Semi-Additive        | No                     | Yes                                | Account Balance         | LAST, MAX, AVG               |
| Non-Additive         | No                     | No                                 | Profit Margin           | N/A (calculated, not summed) |
| Derived (Calculated) | Depends                | Depends                            | Profit (Revenue – Cost) | Calculated                   |

---

### **5. Importance in Data Modeling**

* Correct classification ensures **accurate reporting and aggregation**.
* Influences fact table design and aggregation strategy.
* Helps define correct **ETL transformations** and **business rules**.

---

### **6. Examples of Usage**

| Business Domain | Additive Fact      | Semi-Additive Fact | Non-Additive Fact    | Derived Fact        |
| --------------- | ------------------ | ------------------ | -------------------- | ------------------- |
| Retail          | Units Sold         | Inventory Level    | Return Rate (%)      | Profit              |
| Finance         | Transaction Amount | Account Balance    | Debt-to-Equity Ratio | Net Interest Margin |
| Marketing       | Clicks             | Active Subscribers | Conversion Rate (%)  | ROI                 |

---
