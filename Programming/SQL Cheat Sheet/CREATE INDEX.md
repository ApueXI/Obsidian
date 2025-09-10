---
Created: 2025-09-09T20:18
tags:
  - Indexes
---
## 1. Full Explanation

### 🔹 What is an Index?

- An **index** is a **database structure** that improves the speed of **data retrieval** on a table.
- Think of it like an **index in a book**: helps you find information **faster**.
- Does **not store duplicate data**, but creates a **pointer to the actual rows**.
- Indexes **can slow down INSERT, UPDATE, DELETE** operations because the index needs to be updated.

---

### 🔹 General Syntax

```SQL
-- Create a simple index
CREATE INDEX index_name
ON table_name (column1, column2, ...);

-- Create a unique index
CREATE UNIQUE INDEX index_name
ON table_name (column_name);

-- Create a composite index
CREATE INDEX index_name
ON table_name (column1, column2);

-- Optional: specify index type (DBMS-specific)
CREATE INDEX index_name
ON table_name (column_name)
USING BTREE;  -- MySQL example

```

**Notes:**

- **Unique indexes** prevent duplicate values in the indexed column(s).
- Indexes can be **single-column** or **multi-column (composite)**.
- Some DBMS allow **filtered indexes** or **partial indexes** for specific conditions.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create index|`CREATE INDEX idx_name ON table(col);`|Improves SELECT performance|
|Create unique index|`CREATE UNIQUE INDEX idx_name ON table(col);`|Prevents duplicates|
|Composite index|`CREATE INDEX idx_name ON table(col1, col2);`|Speeds up queries using multiple columns|
|Index type|`USING BTREE / HASH`|DBMS-specific|
|Drop index|`DROP INDEX idx_name;`|Removes index without affecting table|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5000|
|2|Bob|IT|6000|
|3|Charlie|IT|5500|

---

### Step 1: Create a simple index on `name`

```SQL
CREATE INDEX idx_employee_name
ON employees (name);

```

✅ Speeds up queries like:

```SQL
SELECT * FROM employees
WHERE name = 'Bob';

```

---

### Step 2: Create a unique index on `employee_id`

```SQL
CREATE UNIQUE INDEX idx_employee_id
ON employees (employee_id);

```

✅ Ensures **no duplicate employee_id values**.

---

### Step 3: Create a composite index on `department` and `salary`

```SQL
CREATE INDEX idx_dept_salary
ON employees (department, salary);

```

✅ Speeds up queries like:

```SQL
SELECT * FROM employees
WHERE department = 'IT' AND salary > 5500;

```

---

## ✅ Key Takeaways

- `CREATE INDEX` improves **query performance** but may **slow down write operations**.
- Can be **single-column, multi-column, or unique**.
- Choose indexes wisely for **frequently queried columns**.
- Use `DROP INDEX` to remove indexes when no longer needed.
- Indexes are essential for **large tables** and **high-performance databases**.