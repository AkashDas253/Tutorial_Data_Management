## **ETL Transformation**

---

### **1. What is Transformation?**

**Transformation** is the second phase of the ETL process where **raw extracted data** is **cleaned, enriched, formatted, and converted** into a structured and meaningful format suitable for loading into the target system, typically a data warehouse or data lake.

---

### **Purpose of Transformation**

* Ensure data **quality, consistency, and accuracy**
* Apply **business rules** and perform calculations
* Convert data types and formats to match target schema
* Integrate and harmonize data from multiple sources
* Prepare data for **analytics, reporting, or machine learning**

---

### **Common Transformation Tasks**

| Task                                          | Description                                                   |
| --------------------------------------------- | ------------------------------------------------------------- |
| **Data Cleaning**                             | Remove duplicates, handle missing/null values, correct errors |
| **Data Filtering**                            | Exclude irrelevant or invalid records                         |
| **Data Standardization**                      | Uniform formats (e.g., date formats, currencies)              |
| **Data Mapping**                              | Map source fields to target fields                            |
| **Data Aggregation**                          | Summarize data (e.g., totals, averages)                       |
| **Data Splitting**                            | Separate one field into multiple fields                       |
| **Derivation / Calculation**                  | Compute new fields (e.g., profit = revenue - cost)            |
| **Key Generation / Surrogate Keys**           | Create unique IDs for dimension tables                        |
| **Handling Slowly Changing Dimensions (SCD)** | Manage dimension history according to SCD type                |
| **Data Validation**                           | Check data integrity, constraints, and ranges                 |
| **Data Enrichment**                           | Combine with external data (e.g., location from IP)           |
| **Data Sorting**                              | Organize records to support indexing and load requirements    |
| **Data Integration**                          | Merge/join multiple data sources                              |
| **Derived Columns**                           | Compute new fields (e.g., age from DOB)                       |
| **Pivot / Unpivot**                           | Reshape tabular data (wide to long or vice versa)             |

---

### **Transformation Types**

1. **Row-level** – Operations applied on each row independently
2. **Set-level** – Transformations on sets or groups of rows (e.g., aggregations)
3. **Lookup** – Use reference tables to enrich source data
4. **Pivot / Unpivot** – Reshape data structure

---

### **Transformation Logic Implementation**

| Method          | Description                                          |
| --------------- | ---------------------------------------------------- |
| **Declarative** | Drag-drop GUIs in ETL tools                          |
| **Procedural**  | Custom scripts using SQL, Python, Java               |
| **Hybrid**      | Combination of declarative and procedural approaches |

---

### **Common Business Rules in Transformation**

* Replace null values with defaults
* Convert currencies to base units
* Normalize case, trim spaces
* Join lookup tables for code resolution
* Flag based on rules (e.g., high-value customer)

---

### **Advanced Transformations**

| Type                  | Description                                        |
| --------------------- | -------------------------------------------------- |
| **SCD Type 0**        | Retain original value                              |
| **SCD Type 1**        | Overwrite old value                                |
| **SCD Type 2**        | Add new row with historical tracking               |
| **SCD Type 3**        | Store both old and new values in columns           |
| **SCD Type 6**        | Combine features of Types 1, 2, and 3              |
| **Lookups**           | Replace foreign keys/codes with values             |
| **Conditional Logic** | Apply transformations based on business conditions |
| **Normalization**     | Break data into multiple related tables            |
| **Denormalization**   | Flatten data for reporting                         |
| **Metadata Driven**   | Parameterize transformations using metadata        |

---

### **Techniques Used**

* SQL functions (CASE, joins, aggregations)
* User-Defined Functions (UDFs)
* Scripts in Python, Scala, Java (e.g., Pandas, PySpark)
* GUI mappings in tools like Talend, SSIS, Informatica
* Templates for reusable mapping logic
* Conditional branching, loops in ETL pipelines

---

### **Transformation Environment**

| Environment                  | Description                                      |
| ---------------------------- | ------------------------------------------------ |
| **In-Memory Transformation** | In tool’s memory before writing to target        |
| **Pushdown Transformation**  | Push SQL logic to DB layer for performance       |
| **Staging Layer**            | Intermediate area for sequential transformations |

---

### **Key Considerations**

* Ensure **data quality** at each stage
* Optimize for **performance** and **scalability**
* **Document and trace** logic for audit purposes
* Build **modular, reusable components**
* Implement **robust error handling**
* Support **testing** with sample data sets
* Manage **dependencies and transformation order**

---

### **Tools Supporting Transformation**

| Tool Type           | Examples                                         |
| ------------------- | ------------------------------------------------ |
| **ETL Platforms**   | Informatica, Talend, Microsoft SSIS, AWS Glue    |
| **Cloud-native**    | dbt, AWS Glue, Azure Data Factory, Snowflake SQL |
| **Big Data Tools**  | Apache Spark, PySpark, Hive                      |
| **Wrangling Tools** | Trifacta, Alteryx                                |
| **Programming**     | Python (Pandas), Scala, Java                     |

---

### **Best Practices**

* Cleanse data early to prevent downstream issues
* Modularize and reuse transformation components
* Track and version control transformation scripts
* Use logging and alerts for failed records
* Push computation to the source system when beneficial
* Validate transformed data with test cases
* Optimize transformation steps for performance

---

### **Summary**

Transformation is a **critical ETL phase** where **business-ready data** is prepared by applying rules, cleaning, enriching, and integrating raw input. It ensures the loaded data is **reliable, analyzable, and consistent** with business goals.
