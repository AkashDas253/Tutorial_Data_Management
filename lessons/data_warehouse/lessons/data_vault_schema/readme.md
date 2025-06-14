## **Data Vault Schema**

---

### 1. Definition

Data Vault Schema is a **modeling methodology** for **enterprise data warehouses** focusing on **scalability, flexibility, auditability**, combining best features of third normal form (3NF) and dimensional modeling by capturing all raw business data and relationships modularly.

---

### 2. Purpose

* Agile, scalable architecture for complex data environments
* Full historical tracking and audit trails of all changes
* Easy integration of multiple heterogeneous data sources
* Parallel and incremental loading for better performance
* Preserve raw data with full traceability and reprocessing ability

---

### 3. Core Components

| Component     | Description                                                                                                                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hub**       | Stores **unique business keys (natural keys)** with surrogate keys. Represents core business entities (e.g., Customer, Product). Also stores metadata such as load date and record source.        |
| **Link**      | Models **relationships** between hubs (e.g., Customer-Order). Contains surrogate keys from related hubs and metadata fields.                                                                      |
| **Satellite** | Contains **time-variant descriptive attributes**, context, and history for hubs or links. Stores metadata like load timestamps, record source, and effective dates to enable historical tracking. |

---

### 4. Characteristics

* Highly **normalized structure** separating keys (hubs, links) and descriptive data (satellites)
* Handles **historical changes** by storing them in satellites with timestamps
* Supports **parallel, incremental ETL loads** (hubs → links → satellites)
* Maintains **full audit trail** with metadata fields: load date, record source
* **Easily extensible** for new sources or attributes without schema redesign

---

### 5. Comparison with Dimensional Modeling (Star Schema)

| Aspect              | Data Vault                                   | Dimensional Modeling (Star Schema)                   |
| ------------------- | -------------------------------------------- | ---------------------------------------------------- |
| Structure           | Highly normalized (Hubs, Links, Satellites)  | Denormalized (Fact and Dimension tables)             |
| Historical Tracking | Stored in satellites with full timestamps    | Slowly Changing Dimensions (SCDs)                    |
| Flexibility         | High, easy to add new data and relationships | Moderate, requires redesign for major schema changes |
| Source Data Storage | Raw, stores all source data                  | Transformed and cleansed for analysis                |
| Loading             | Parallel and incremental                     | Often batch processing                               |
| Auditability        | Built-in with metadata and timestamps        | Limited                                              |

---

### 6. Typical Metadata Fields (in all components)

* `Load_Date` — Timestamp when data was loaded into the warehouse
* `Record_Source` — Origin system of the data
* `Effective_Date` (usually satellites) — Validity start date of the attribute values

---

### 7. Example

**Hub\_Customer**

| Customer\_Hub\_Key (PK) | Customer\_ID (Natural Key) | Load\_Date | Record\_Source |
| ----------------------- | -------------------------- | ---------- | -------------- |
| 1                       | CUST1001                   | 2025-06-01 | CRM System     |
| 2                       | CUST1002                   | 2025-06-01 | CRM System     |

**Hub\_Product**

| Product\_Hub\_Key (PK) | Product\_ID (Natural Key) | Load\_Date | Record\_Source |
| ---------------------- | ------------------------- | ---------- | -------------- |
| 10                     | PROD2001                  | 2025-06-01 | ERP System     |
| 11                     | PROD2002                  | 2025-06-01 | ERP System     |

**Link\_Order**

| Order\_Link\_Key (PK) | Customer\_Hub\_Key (FK) | Product\_Hub\_Key (FK) | Load\_Date | Record\_Source |
| --------------------- | ----------------------- | ---------------------- | ---------- | -------------- |
| 100                   | 1                       | 10                     | 2025-06-01 | Sales System   |
| 101                   | 2                       | 11                     | 2025-06-01 | Sales System   |

**Satellite\_Customer**

| Customer\_Hub\_Key (FK) | Name         | Region | Effective\_Date | Load\_Date | Record\_Source |
| ----------------------- | ------------ | ------ | --------------- | ---------- | -------------- |
| 1                       | John Doe     | East   | 2025-06-01      | 2025-06-01 | CRM System     |
| 1                       | John Doe Jr. | East   | 2025-06-15      | 2025-06-15 | CRM System     |
| 2                       | Jane Smith   | West   | 2025-06-01      | 2025-06-01 | CRM System     |

* Hubs store unique business keys with metadata
* Links store relationships between hubs
* Satellites store descriptive, historical attributes with timestamps

---

### 8. Benefits

* Scalable and flexible for enterprise-level data warehouses
* Full historical tracking with detailed audit metadata
* Easy integration of multiple source systems
* Supports parallel ETL processing for faster loads
* Preserves raw data for traceability and reprocessing

---

### 9. Challenges

* More complex schema with more tables and joins
* Requires more storage for normalized data and history
* Query complexity higher due to multiple joins
* Requires skilled design and ETL orchestration

---

### 10. When to Use Data Vault

* Large, complex, evolving data environments
* Need for comprehensive auditability and historical tracking
* Integration of multiple heterogeneous data sources
* Agile, incremental data warehouse development

---
