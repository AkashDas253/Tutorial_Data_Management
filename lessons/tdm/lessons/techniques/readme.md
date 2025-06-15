## TDM Techniques

---

### **Overview**

Test Data Management (TDM) techniques are the methods used to create, manipulate, deliver, and secure test data across testing phases. These techniques ensure test data is relevant, compliant, and optimized for test objectives.

---

### **Key TDM Techniques**

| **Technique**                 | **Description**                                                                                                                                                                                                |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Data Subsetting**           | Extracts a smaller, representative portion of production data while maintaining referential integrity. Reduces storage and speeds up test execution.                                                           |
| **Data Masking**              | Obfuscates sensitive or confidential data (e.g., PII) to ensure privacy and regulatory compliance. Includes static, dynamic, and on-the-fly masking using techniques like shuffling, encryption, tokenization. |
| **Synthetic Data Generation** | Creates artificial data based on rules, patterns, or statistical models. Useful for generating edge cases, negative scenarios, or data not present in production.                                              |
| **Data Cloning**              | Duplicates test datasets across different test environments or teams. Ensures consistent testing conditions. Often used in sandbox environments.                                                               |
| **Data Virtualization**       | Provides virtual, real-time access to source data without creating physical copies. Enables efficient, read-only access to up-to-date information.                                                             |
| **Test Data Reservation**     | Reserves specific test data instances for certain test cases or teams to avoid conflicts and ensure uniqueness in shared environments.                                                                         |
| **Data Profiling**            | Analyzes the structure, content, and quality of source data. Helps in identifying patterns, constraints, anomalies, and relationships.                                                                         |
| **Data Refreshing**           | Periodically updates or reloads test data to keep it relevant and aligned with production or business changes.                                                                                                 |
| **Test Data Validation**      | Ensures that the test data is accurate, complete, and logically consistent before use. Validates schema, format, constraints, and integrity.                                                                   |

---
