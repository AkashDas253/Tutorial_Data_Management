## Conformed Dimensions

---

### 1. Definition

A **Conformed Dimension** is a dimension that is **shared across multiple fact tables or data marts** and maintains the **same structure, content, and meaning**. It allows consistent analysis across different business processes.

---

### 2. Purpose

* Ensure **consistency** in reporting and analytics
* Enable **integration** across different subject areas
* Allow **cross-functional analysis** (e.g., sales vs. inventory by the same customer)

---

### 3. Characteristics

| Feature                  | Description                                                     |
| ------------------------ | --------------------------------------------------------------- |
| **Shared**               | Used by multiple fact tables or data marts                      |
| **Consistent Structure** | Same column names, definitions, and keys                        |
| **Business-Aligned**     | Reflects core business entities (e.g., customer, product, time) |
| **Global Scope**         | Used across different departments or functions                  |
| **Stable & Reusable**    | Changes managed centrally to maintain consistency               |

---

### 4. Common Examples

| Dimension Type | Use Case Example                           |
| -------------- | ------------------------------------------ |
| Time           | Shared across order, shipment, inventory   |
| Customer       | Used in sales, service, billing data marts |
| Product        | Used in procurement, sales, inventory      |
| Geography      | Used across marketing, sales, delivery     |

---

### 5. Types of Conformance

| Type                     | Description                                                                   |
| ------------------------ | ----------------------------------------------------------------------------- |
| **Physically Conformed** | Exactly the same table used in different star schemas                         |
| **Logically Conformed**  | Views or aliases are used, with same definitions but different physical forms |

---

### 6. Example

**Shared `customer_dim` table used in both `sales_fact` and `support_fact`**:

```sql
-- Used in sales
SELECT customer_name, SUM(sales_amount)
FROM sales_fact sf
JOIN customer_dim cd ON sf.customer_key = cd.customer_key
GROUP BY customer_name;

-- Used in support
SELECT customer_name, COUNT(ticket_id)
FROM support_fact sf
JOIN customer_dim cd ON sf.customer_key = cd.customer_key
GROUP BY customer_name;
```

Both queries interpret the **customer** in the same way due to conformed dimension.

---

### 7. Benefits

* **Single version of truth** for business entities
* Simplifies **data integration** across domains
* Reduces redundancy and improves **governance**
* Enhances **reporting accuracy** and trust in analytics

---

### 8. Challenges

* Requires **tight data governance and coordination**
* More **complex to maintain** in decentralized teams
* Changes in structure or definition must be **carefully managed**

---

### 9. Best Practices

* Define **clear data ownership** for conformed dimensions
* Use **data dictionaries** and metadata tools to document structure
* Regularly **synchronize** and validate shared dimensions across systems
* Adopt **master data management (MDM)** if scale demands

---
