## Data Subsetting in Test Data Management (TDM)

---

### Definition

**Data Subsetting** is the process of extracting a smaller, representative portion of a larger data source while preserving data integrity, relationships, and diversity. It is used to reduce test data volume while maintaining quality and coverage for testing.

---

### Purpose

* Minimize test data size for faster testing
* Reduce infrastructure and storage costs
* Avoid exposing full production datasets
* Improve performance of test environments
* Enable targeted testing for specific use cases

---

### Key Characteristics

| Aspect                    | Description                                                          |
| ------------------------- | -------------------------------------------------------------------- |
| **Representative**        | Maintains key data characteristics and distributions from full data  |
| **Referential Integrity** | Ensures foreign-key and parent-child relationships are preserved     |
| **Consistent**            | Keeps logical consistency across multiple related tables or entities |
| **Customizable**          | Allows subsetting based on filters, date ranges, business logic      |

---

### Types of Subsetting

| Type                      | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| **Static Subsetting**     | One-time extraction of subset from source                         |
| **Dynamic Subsetting**    | On-demand subsetting based on changing criteria                   |
| **Rule-Based Subsetting** | Uses business rules or filters (e.g., all orders from last month) |
| **Metadata-Driven**       | Uses metadata to determine relevant data paths                    |
| **Relationship-Aware**    | Includes all child and parent records automatically               |
| **Test-Case Specific**    | Subsets created for individual test scenarios                     |

---

### Techniques and Approaches

* **Top-down Subsetting**: Begin with primary entities and extract related data down the relationship tree
* **Bottom-up Subsetting**: Begin with specific data needed for test cases and backtrack necessary dependencies
* **Data Classification**: Categorize data into critical, sensitive, or frequently accessed before subsetting
* **Sampling**: Use statistical or stratified sampling to ensure data variety
* **Filtering**: Apply where conditions like region, product type, or transaction status
* **Cloning with Filters**: Copy a filtered portion of the data along with constraints and dependencies

---

### Tools and Automation Support

* **Commercial**: Informatica TDM, CA Test Data Manager, IBM Optim, Delphix
* **Open Source / Scripts**: SQL scripts, Jailer, DataBee
* **Features**:

  * Data model discovery
  * Referential integrity enforcement
  * Masking integration
  * Automation hooks (API, CLI, CI/CD)

---

### Benefits

* Faster data provisioning
* Improved test efficiency
* Better focus on relevant test cases
* Reduced resource consumption
* Easier compliance and masking enforcement
* Enables parallel testing and data isolation

---

### Challenges

| Challenge                     | Description                                                           |
| ----------------------------- | --------------------------------------------------------------------- |
| **Maintaining Integrity**     | Risk of orphaned or broken foreign key relationships                  |
| **Data Skew**                 | Non-representative sampling may miss edge cases                       |
| **Cross-System Dependencies** | Difficult if related data exists in multiple systems                  |
| **Subset Refresh Complexity** | Refreshing subsets while preserving sync and consistency              |
| **High Initial Setup**        | Complex subsetting logic may need modeling tools and metadata mapping |

---

### Best Practices

* Profile and analyze data before designing subsets
* Always maintain referential and business integrity
* Align subsetting logic with test coverage goals
* Integrate masking with subsetting when needed
* Document rules and filters used for reproducibility
* Automate subsetting as part of CI/CD where possible
