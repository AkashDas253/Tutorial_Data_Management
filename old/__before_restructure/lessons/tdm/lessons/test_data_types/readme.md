## Types of Test Data

---

### **Overview**

Test data refers to the input data used to validate software behavior during testing. Each type of test data serves a specific purpose and testing goal—ensuring functionality, security, performance, or robustness.

---

### **Types of Test Data**

| Type of Test Data         | Description                                                                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Static Data**           | Predefined, unchanging data used across multiple test cycles (e.g., lookup tables, configuration values).                             |
| **Transactional Data**    | Dynamic, event-based data representing user or system operations (e.g., orders, payments, log entries).                               |
| **Master Data**           | Core business entities used across systems (e.g., customer profiles, product catalog, employee records).                              |
| **Synthetic Data**        | Artificially created data used when real data is unavailable, incomplete, or for edge cases. Often used in automation and AI testing. |
| **Masked Data**           | Production data with sensitive values (e.g., PII, PHI) obfuscated to protect privacy and comply with regulations.                     |
| **Negative Data**         | Invalid, incorrect, or boundary-pushing inputs used to test system error handling and validation.                                     |
| **Positive Data**         | Valid inputs that represent expected, successful flows to verify system correctness.                                                  |
| **Boundary Data**         | Data at the edge of acceptable input ranges, such as max/min values, used to test limits.                                             |
| **Invalid Data**          | Data types or formats that violate expected constraints (e.g., string in a numeric field, malformed JSON).                            |
| **Null/Empty Data**       | Used to test system behavior with missing or null values.                                                                             |
| **Automated Test Data**   | Data generated or maintained automatically as part of test scripts in CI/CD pipelines.                                                |
| **Performance Test Data** | Large-volume data used to simulate load, concurrency, and stress scenarios.                                                           |

---

### **Special Categories**

| Category               | Details                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Compliance Data**    | Contains sensitive information that must follow legal regulations (e.g., GDPR, HIPAA). Often masked or anonymized. |
| **Regression Data**    | Stable, version-controlled data reused for repeatable regression testing across software versions.                 |
| **Integration Data**   | Linked datasets across modules or services used in integration testing.                                            |
| **UAT Data**           | Realistic data used by business users during User Acceptance Testing (UAT) for validating workflows.               |
| **Training Data (ML)** | For ML systems: structured data labeled and formatted for training/testing AI models.                              |

---

### **Test Data by Usage in Testing Phases**

| Testing Phase       | Relevant Test Data                 |
| ------------------- | ---------------------------------- |
| Unit Testing        | Mock data, small inputs            |
| Integration Testing | Linked transactional + master data |
| System Testing      | Full datasets, realistic volumes   |
| Regression Testing  | Version-controlled stable data     |
| Performance Testing | Large-scale, concurrent data       |
| Security Testing    | Masked sensitive data              |
| Negative Testing    | Invalid, edge-case, null data      |

---
