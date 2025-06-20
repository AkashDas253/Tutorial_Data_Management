## Core Components of Test Data Management (TDM)

---

### **1. Data Sources**

* Origin of test data used in the system.
* Can include:

  * Production databases
  * Staging environments
  * Flat files (CSV, JSON, XML)
  * APIs or external systems
  * Synthetic data repositories

---

### **2. Data Subsetting**

* Extracting a representative portion of production data.
* Reduces size while retaining referential integrity and test coverage.
* Ensures faster test execution and lower storage costs.

---

### **3. Data Masking**

* Protects sensitive data by transforming it into unidentifiable values.
* Ensures compliance with privacy regulations like GDPR, HIPAA.
* Types:

  * **Static masking** – Once at rest (used for copies)
  * **Dynamic masking** – Real-time during access
  * **Tokenization, Shuffling, Encryption, Nulling** as techniques

---

### **4. Test Data Generation**

* Creates synthetic data based on business rules and test scenarios.
* Useful when:

  * Production data is incomplete
  * Negative/edge test cases are required
  * Real data can't be used due to compliance
* Can be rule-based or AI-driven.

---

### **5. Data Provisioning**

* Delivering the prepared data to testing environments.
* Supports:

  * Environment-specific configuration
  * On-demand or scheduled delivery
  * Integration with CI/CD pipelines

---

### **6. Data Refreshing**

* Regularly updating test data to keep it relevant and accurate.
* Prevents stale or outdated test runs.
* Involves re-extraction, regeneration, or syncing with source systems.

---

### **7. Version Control**

* Maintains different versions of test datasets.
* Allows rollback to previous states.
* Supports auditability, repeatable test runs, and comparison testing.

---

### **8. Environment Synchronization**

* Ensures test data aligns with configuration of target environments.
* Maintains:

  * Schema compatibility
  * Application version alignment
  * Cross-environment data consistency

---

### **9. Data Archiving and Retention**

* Archives old test datasets for audit, compliance, or reuse.
* Defines retention policies for temporary or sensitive data.

---

### **10. Data Discovery and Profiling**

* Analyzes source data for:

  * Patterns
  * Relationships
  * Data quality issues
* Helps in defining accurate subsetting and masking rules.

---
