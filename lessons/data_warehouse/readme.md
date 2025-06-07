## **Data Warehouse**

---

### **1. What is a Data Warehouse?**

A **data warehouse (DW)** is a **centralized repository** that stores **integrated**, **historical**, and **subject-oriented** data from multiple sources for **reporting**, **analysis**, and **decision-making**.

---

### **2. Key Characteristics**

| Characteristic       | Description                                           |
| -------------------- | ----------------------------------------------------- |
| **Subject-Oriented** | Organized around key subjects (e.g., customer, sales) |
| **Integrated**       | Combines data from multiple heterogeneous sources     |
| **Non-volatile**     | Once data is loaded, it is not changed                |
| **Time-variant**     | Historical data is stored for trend analysis          |

---

### **3. Components of Data Warehouse**

| Component          | Description                                                          |
| ------------------ | -------------------------------------------------------------------- |
| **Source Systems** | OLTP systems, CRM, ERP, flat files, etc.                             |
| **ETL Process**    | Extract, Transform, Load: moves data from source to DW               |
| **Staging Area**   | Temporary storage for data cleansing and transformation              |
| **Data Warehouse** | Central repository for structured, historical data                   |
| **Data Marts**     | Subsets of data warehouse for specific departments (e.g., HR, Sales) |
| **Metadata**       | Data about data (source, update time, transformation logic)          |
| **OLAP Tools**     | Used for multidimensional analysis, slicing and dicing data          |
| **BI Tools**       | Reporting and visualization tools (e.g., Tableau, Power BI)          |

---

### **4. Architecture Types**

| Architecture    | Description                                                |
| --------------- | ---------------------------------------------------------- |
| **Single-Tier** | All layers combined (not recommended for large systems)    |
| **Two-Tier**    | Separate DW and user interface (less scalable)             |
| **Three-Tier**  | Most common: Staging → Data Warehouse → Presentation Layer |

---

### **5. Data Warehouse Schemas**

* **Star Schema**: Central fact table with denormalized dimension tables
* **Snowflake Schema**: Normalized dimension tables
* **Fact Constellation (Galaxy)**: Multiple fact tables sharing dimensions

---

### **6. Data Warehouse vs Database**

| Feature          | Data Warehouse         | OLTP Database           |
| ---------------- | ---------------------- | ----------------------- |
| Purpose          | Analysis and reporting | Daily operations        |
| Data Type        | Historical             | Current                 |
| Normalization    | Denormalized           | Highly normalized       |
| Query Type       | Complex reads          | Simple reads and writes |
| Performance Goal | High-speed reads       | High-speed transactions |

---

### **7. ETL Process**

| Step          | Description                               |
| ------------- | ----------------------------------------- |
| **Extract**   | Retrieve data from multiple sources       |
| **Transform** | Cleanse, format, and apply business rules |
| **Load**      | Store into the data warehouse             |

---

### **8. OLAP (Online Analytical Processing)**

* Supports **multidimensional analysis**
* Enables slicing, dicing, pivoting, drill-down, and roll-up
* Types:

  * **ROLAP** (Relational OLAP)
  * **MOLAP** (Multidimensional OLAP)
  * **HOLAP** (Hybrid OLAP)

---

### **9. Data Marts**

| Type            | Description                                         |
| --------------- | --------------------------------------------------- |
| **Dependent**   | Sourced from central data warehouse                 |
| **Independent** | Standalone; built from specific operational systems |
| **Hybrid**      | Combination of both                                 |

---

### **10. Metadata**

* **Technical Metadata**: Source, schema, data types
* **Business Metadata**: Business definitions and meanings
* **Operational Metadata**: ETL logs, refresh times

---

### **11. Data Governance in DW**

* Data quality assurance
* Access control and security
* Compliance (e.g., GDPR)

---

### **12. Use Cases**

* Trend analysis
* Forecasting
* Performance tracking
* Executive dashboards

---

### **13. Benefits**

* Improved decision-making
* Faster reporting
* Data consistency
* Historical insight

---

### **14. Challenges**

* High initial cost and complexity
* ETL and data consistency issues
* Ongoing maintenance

---
