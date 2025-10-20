## TDM in Testing Stages

---

### **Overview**

Test Data Management (TDM) supports different stages of software testing by providing appropriate, reliable, and secure data tailored to each testing type. Each stage has specific data needs, formats, and quality expectations.

---

### **Test Data Management (TDM) in Testing Stages**

| **Testing Stage**              | **TDM Requirements and Responsibilities**                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Unit Testing**               | - Minimal, isolated datasets<br>- Use of mock or stub data<br>- Quick to load and reset<br>- Ideal for automation and early validation                   |
| **Integration Testing**        | - Data simulating interaction between components<br>- Must maintain referential integrity<br>- Cross-entity linking (e.g., users → orders)               |
| **System Testing**             | - Full-scale, end-to-end datasets<br>- Covers all modules and workflows<br>- Realistic test data volume and variety                                      |
| **Regression Testing**         | - Stable, version-controlled data<br>- Ensures repeatability of test results<br>- Prevents false positives from data changes                             |
| **User Acceptance Testing**    | - Business-like datasets (masked production data)<br>- Validates functionality from end-user perspective<br>- Covers real-world scenarios and edge cases |
| **Performance / Load Testing** | - Large-scale, production-like datasets<br>- Designed for concurrency and stress testing<br>- Supports load simulation and bottleneck analysis           |
| **Security Testing**           | - Sensitive data handled securely (masked/anonymized)<br>- Data scenarios for testing injection, access control, leakage prevention                      |
| **Negative Testing**           | - Invalid, edge, or unexpected input data<br>- Tests system’s error handling, validation mechanisms                                                      |
| **Compliance Testing**         | - Data must conform to privacy laws (e.g., GDPR, HIPAA)<br>- Masked or anonymized PII used for legal and ethical compliance                              |

---

### **Key Considerations in TDM for Testing**

* **Data availability**: On-demand access during test execution.
* **Data consistency**: Cross-module data integrity.
* **Environment alignment**: Matching test data to test environment setup.
* **Automation readiness**: Test data compatible with CI/CD pipelines.

---
