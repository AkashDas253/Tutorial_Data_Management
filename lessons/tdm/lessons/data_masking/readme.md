## Data Masking in TDM

---

### **Overview**

**Data Masking** is a TDM technique used to **obscure sensitive or personally identifiable information (PII)** in non-production environments while preserving data format and usability. It is vital for **data privacy**, **regulatory compliance**, and **security during testing**.

---

### **Objectives of Data Masking**

* Protect confidential and sensitive data (e.g., names, SSNs, credit card numbers).
* Enable testing on real-like data without exposing actual information.
* Ensure compliance with regulations like **GDPR**, **HIPAA**, **PCI DSS**, **CCPA**.
* Prevent internal data breaches or misuse in test environments.

---

### **Types of Data Masking**

| **Type**                      | **Description**                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Static Data Masking**       | Applies masking to a static copy of the data stored in a test database.                                  |
| **Dynamic Data Masking**      | Masks data in real-time as it is retrieved by unauthorized users without altering the original database. |
| **On-the-fly Masking**        | Applies masking during data transfer or ETL without persisting the masked data.                          |
| **Deterministic Masking**     | Replaces the same input value with the same masked value every time.                                     |
| **Non-deterministic Masking** | Generates random output values that are different for each run.                                          |

---

### **Common Data Masking Techniques**

| **Technique**        | **Description**                                                         |
| -------------------- | ----------------------------------------------------------------------- |
| **Substitution**     | Replaces real values with realistic fake data (e.g., names with names). |
| **Shuffling**        | Randomizes data within the same column or set.                          |
| **Encryption**       | Converts data into ciphertext; reversible with keys.                    |
| **Tokenization**     | Replaces real values with mapped tokens; requires secure mapping.       |
| **Nulling Out**      | Replaces sensitive values with null or blank entries.                   |
| **Data Variance**    | Adds random noise to data (e.g., changing salary slightly).             |
| **Masking Patterns** | Keeps format but hides part of data (e.g., ****-****-1234).             |
| **Blurring**         | Groups similar data into general ranges (e.g., age 20–30).              |

---

### **Popular Data Masking Tools**

| Tool                                   | Description                                                         |
| -------------------------------------- | ------------------------------------------------------------------- |
| **Informatica TDM**                    | Offers static/dynamic masking, subsetting, and compliance features. |
| **Delphix**                            | Provides data virtualization with integrated masking.               |
| **CA Test Data Manager (Broadcom)**    | Advanced rule-based masking with synthetic data support.            |
| **IBM InfoSphere Optim**               | Database-centric masking, encryption, and archiving.                |
| **Redgate Data Masker**                | SQL Server masking with predefined rules.                           |
| **Oracle Data Masking and Subsetting** | Integrated with Oracle DB for secure test environments.             |

---

### **Regulatory Requirements Supported**

| Regulation  | Data Masking Role                                      |
| ----------- | ------------------------------------------------------ |
| **GDPR**    | Anonymization and pseudonymization of EU citizen data. |
| **HIPAA**   | Mask PHI (Personal Health Information).                |
| **PCI DSS** | Mask credit card and payment data.                     |
| **CCPA**    | Hide Californian consumer identity details.            |

---

### **Best Practices for Data Masking**

* Classify and identify sensitive data fields before masking.
* Use deterministic masking where data correlation is necessary (e.g., joins).
* Automate masking as part of data provisioning pipelines.
* Maintain referential integrity across tables.
* Document and audit all masking rules and access logs.
* Avoid re-identification risks—don’t retain mapping for tokenized data unless needed.

---
