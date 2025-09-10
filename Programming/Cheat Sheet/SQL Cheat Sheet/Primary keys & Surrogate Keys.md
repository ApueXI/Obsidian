---
Created: 2025-09-09T20:29
tags:
  - Normalization-&-Database-Design
---
## 1. Full Explanation

### 🔹 Primary Key (PK)

- A **primary key** uniquely identifies each row in a table.
- Can be **single-column** or **composite (multi-column)**.
- Enforces **uniqueness** and **NOT NULL** constraint automatically.

**Characteristics:**

- Each table can have **only one primary key**.
- Often used as **foreign keys** in other tables.

**Syntax:**

```SQL
-- Single-column primary key
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50)
);

-- Composite primary key
CREATE TABLE Enrollment (
    student_id INT,
    course_id INT,
    PRIMARY KEY(student_id, course_id)
);

```

---

### 🔹 Surrogate Key

- A **surrogate key** is an **artificial key** created to uniquely identify a row.
- Usually **auto-incremented numbers** (`INT`, `BIGINT`) or **UUIDs**.
- **No business meaning**; used purely for uniqueness.

**Why Use Surrogate Keys?**

1. Simplifies primary key for large/composite natural keys.
2. Avoids problems when **natural keys change**.
3. Improves **performance** for joins and indexing.

**Syntax:**

```SQL
-- Auto-increment surrogate key
CREATE TABLE Employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50)
);

-- UUID surrogate key
CREATE TABLE Orders (
    order_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    customer_id INT,
    total DECIMAL(10,2)
);

```

---

## 2. Comparison Table

|Feature|Primary Key (Natural)|Surrogate Key|
|---|---|---|
|Purpose|Unique identifier based on real data|Unique artificial identifier|
|Meaning|Business meaning|No business meaning|
|Type|Existing column(s)|Auto-generated (INT/UUID)|
|Stability|Can change if business data changes|Never changes|
|Performance|May be slower if composite or string|Faster (integer, simple)|
|Example|`SSN`, `Email`|`employee_id`, `order_id`|

---

## 3. Real-World Example

**Scenario:** Employee table

### Using a Natural Primary Key

```SQL
CREATE TABLE Employees (
    ssn CHAR(9) PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50)
);

```

- `ssn` uniquely identifies employees, but may have issues if **format changes or privacy rules apply**.

### Using a Surrogate Key

```SQL
CREATE TABLE Employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    ssn CHAR(9),
    name VARCHAR(50),
    department VARCHAR(50)
);

```

- `employee_id` is **stable, simple, and efficient** for joins.
- `ssn` can still be unique with a **UNIQUE constraint** if needed:

```SQL
ALTER TABLE Employees ADD CONSTRAINT unique_ssn UNIQUE(ssn);

```

---

## ✅ Key Takeaways

- **Primary Key:** uniquely identifies rows, may be **natural** or **composite**.
- **Surrogate Key:** artificial, stable, and performance-friendly identifier.
- Surrogate keys are widely used in **modern relational databases**, especially when natural keys are **large, composite, or unstable**.
- Best practice: **use surrogate keys as primary keys** and enforce **natural uniqueness** separately.