## Factless Fact Tables

---

### 1. Definition

A **Factless Fact Table** is a type of fact table that does **not contain any measurable or numeric facts**. Instead, it only contains **foreign keys** referencing dimension tables and is used to **capture events or record conditions**.

---

### 2. Purpose

* Track the **occurrence of events** without metrics
* Capture **many-to-many relationships** between dimensions
* Support **analysis of event frequencies, participation, or non-events**

---

### 3. Characteristics

| Feature                 | Description                                                                         |
| ----------------------- | ----------------------------------------------------------------------------------- |
| No numeric measures     | Contains only foreign keys to dimension tables                                      |
| Event or coverage-based | Designed to track events (e.g., student attendance) or coverage (e.g., eligibility) |
| Can be additive         | Counts can be aggregated using `COUNT(*)`                                           |
| Efficient for auditing  | Captures important non-measurable business processes                                |

---

### 4. Types of Factless Fact Tables

| Type               | Description                                               | Example                                        |
| ------------------ | --------------------------------------------------------- | ---------------------------------------------- |
| **Event Tracking** | Captures events that occurred                             | Student attended a class                       |
| **Coverage**       | Captures allowable or expected relationships (non-events) | Student enrolled in course, but may not attend |

---

### 5. Example

#### 5.1 Event Tracking Example: Student Attendance

**Fact\_Student\_Attendance**

| Student\_ID (FK) | Class\_ID (FK) | Date       |
| ---------------- | -------------- | ---------- |
| 101              | CSE101         | 2025-06-05 |
| 102              | CSE101         | 2025-06-05 |
| 101              | CSE102         | 2025-06-06 |

You can then calculate:

```sql
SELECT Class_ID, COUNT(*) AS attendance_count
FROM Fact_Student_Attendance
GROUP BY Class_ID;
```

#### 5.2 Coverage Example: Course Enrollment

**Fact\_Course\_Enrollment**

| Student\_ID (FK) | Course\_ID (FK) |
| ---------------- | --------------- |
| 101              | CSE101          |
| 101              | CSE102          |
| 102              | CSE101          |

This helps identify:

* Who **was eligible** to attend a course
* Who **did not attend** (by comparing with event table)

---

### 6. Use Cases

* Attendance tracking (students, employees)
* Marketing campaigns (customer exposed to ad)
* Healthcare eligibility (patients entitled to services)
* HR policies (employee assigned to training)

---

### 7. Benefits

* **Lightweight** and easy to maintain
* Captures important **business events or conditions**
* Facilitates **gap analysis** (e.g., eligible vs. actual participation)
* Supports **compliance and auditing**

---

### 8. Challenges

* May be **confusing without measures**
* Requires **clear documentation** of its purpose
* Might need **cross-table queries** to derive metrics

---

### 9. Best Practices

* Use **clear and meaningful dimension keys**
* Document the **business event or rule** being captured
* Combine with other facts when necessary for full context
* Optimize indexing for **fast COUNT or JOIN operations**

---
