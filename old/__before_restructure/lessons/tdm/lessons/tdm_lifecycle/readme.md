## Test Data Management (TDM) Lifecycle Phases

---

### **Overview**

The TDM lifecycle defines the structured process to manage test data from requirement gathering to retirement. It ensures the availability of high-quality, secure, and relevant data throughout the software testing lifecycle.

---

### **Test Data Management (TDM) Lifecycle Phases**

| **Phase**                         | **Description**                                                                                                                                                                 |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Requirement Analysis**          | - Identify test data needs based on test cases and business logic.<br>- Define data volume, types, structure, and relationships.<br>- Collaborate with QA, developers, and BAs. |
| **Data Design**                   | - Design schemas, relationships, and constraints for test data.<br>- Decide between static and dynamic data.<br>- Ensure compatibility with test environments.                  |
| **Data Extraction**               | - Extract data from production, staging, or legacy systems.<br>- Use subsetting and filtering for relevant test data.<br>- Preserve referential integrity.                      |
| **Data Masking / Transformation** | - Mask or anonymize sensitive data (PII, PHI).<br>- Apply transformations to meet test requirements.<br>- Ensure compliance with privacy regulations.                           |
| **Data Generation**               | - Generate synthetic data to cover missing, negative, and edge cases.<br>- Use AI-based, random, or rule-driven techniques.<br>- Fill gaps where real data is unavailable.      |
| **Data Provisioning**             | - Deliver prepared data to appropriate test environments.<br>- Automate data loading and rollback processes.<br>- Manage environment-specific configurations.                   |
| **Data Maintenance & Refresh**    | - Regularly refresh or update stale data.<br>- Clean up old or obsolete datasets.<br>- Maintain version control and audit trails.                                               |
| **Data Archival / Retirement**    | - Archive datasets for future use, audit, or compliance.<br>- Define retention policies.<br>- Securely delete expired or sensitive data.                                        |

---

### **Optional/Supporting Activities**

* **Data Profiling & Discovery** – Understand source data characteristics, quality, and structure.
* **Test Data Reservation** – Reserve critical data to prevent conflicts in shared test environments.
* **Test Data Validation** – Ensure accuracy, integrity, and completeness of provisioned data.

---
