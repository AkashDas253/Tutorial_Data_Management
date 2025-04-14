## 📘 Schema Design in Data Warehousing

---

### **Definition**

**Schema design** in data warehousing refers to the logical arrangement of tables in a database to support efficient data storage, retrieval, and analysis. It defines how data is structured and related, playing a critical role in performance and usability of the data warehouse.

---

### **Purpose**

- Organize data for efficient **reporting and analysis**
- Ensure **data integrity** and **consistency**
- Enable **faster query performance**
- Support **OLAP operations** such as slicing, dicing, drilling down, and pivoting
- Facilitate **maintainability** and **scalability** of the data warehouse

---

### **Types of Schemas**

| Schema Type      | Description |
|------------------|-------------|
| **Star Schema**  | Central fact table connected to multiple dimension tables |
| **Snowflake Schema** | Extension of star schema with normalized dimensions (dimensions split into sub-dimensions) |
| **Galaxy Schema** (Fact Constellation) | Multiple fact tables sharing dimension tables |
| **Normalized Schema** | Highly normalized, reduces redundancy, used in some data warehouses |
| **Denormalized Schema** | Data duplication allowed for simplicity and performance in querying |

---

### **1. Star Schema**

- **Structure**:
  - One central **Fact Table**
  - Multiple **Dimension Tables** directly connected to the fact table
- **Features**:
  - Denormalized dimensions
  - Simple and faster for queries
  - Ideal for slicing and dicing in OLAP

**Example**:
```
Sales Fact Table → Date, Product, Customer, Store (foreign keys), Revenue, Quantity
```

---

### **2. Snowflake Schema**

- **Structure**:
  - Fact table connected to normalized dimension tables
  - Dimension tables may have sub-dimensions
- **Features**:
  - Normalized dimensions reduce redundancy
  - More complex joins but saves storage
  - Useful when dimension tables have hierarchical relationships

**Example**:
```
Product → Subcategory → Category
```

---

### **3. Galaxy Schema**

- **Structure**:
  - Multiple Fact Tables
  - Shared Dimension Tables
- **Features**:
  - Supports complex business scenarios
  - Facilitates analysis from multiple fact perspectives
  - Suitable for integrated enterprise data warehouses

**Example**:
```
Sales Fact, Inventory Fact sharing Product, Store, and Date dimensions
```

---

### **Schema Design Elements**

#### **Fact Table**
- Contains:
  - **Foreign keys** to dimension tables
  - **Numeric measures** (quantitative data)
- Characteristics:
  - Large in size
  - Central to schema

#### **Dimension Table**
- Contains:
  - Descriptive attributes (textual or categorical)
  - Hierarchies (e.g., Year → Quarter → Month → Day)
- Characteristics:
  - Smaller in size
  - Used for filtering, grouping, and labeling

---

### **Schema Design Considerations**

| Factor | Description |
|--------|-------------|
| **Business Requirements** | Understand reporting and analytical needs |
| **Granularity** | Decide the level of detail in the fact table (e.g., daily, monthly, transactional) |
| **Historical Data** | Plan for historical changes in dimension attributes (slowly changing dimensions) |
| **Query Performance** | Optimize for common queries and aggregation |
| **Storage and Maintenance** | Balance normalization and denormalization based on system capabilities |

---

### **Best Practices**

- Use **star schema** where possible for performance and simplicity
- Apply **snowflake schema** when dimension tables are too large or have natural hierarchies
- Design **dimension hierarchies** explicitly for drill-down operations
- Index foreign keys and use **surrogate keys**
- Keep **fact table grain consistent**
- Implement **slowly changing dimension** strategies (Type 1, 2, 3, etc.)
- Plan for **data partitioning** and **aggregation tables** to improve performance

---
