---
Created: 2025-09-09T20:15
tags:
  - Views
---
## 1. Full Explanation

### 🔹 What is an Updatable View?

- An **updatable view** is a view through which you can **perform** `**INSERT**`**,** `**UPDATE**`**, or** `**DELETE**` **operations**.
- Changes **propagate to the underlying base tables**.
- **Not all views are updatable**; limitations apply depending on **DBMS and view complexity**.

---

### 🔹 Rules for Updatable Views (General)

1. Must reference **only one base table** (simple view).
2. Cannot include:
    - `GROUP BY`, `HAVING`, or aggregate functions.
    - `DISTINCT` or `UNION`.
    - Joins (some DBMS allow **INSTEAD OF triggers** for joined views).
3. Cannot reference **computed columns** unless **insertable expressions** are allowed.
4. Can include `WHERE` for filtering, but inserting rows must satisfy underlying table constraints.

---

### 🔹 General Syntax

```SQL
-- Update rows through a view
UPDATE view_name
SET column1 = value1, column2 = value2
WHERE condition;

-- Insert rows through a view
INSERT INTO view_name (column1, column2)
VALUES (value1, value2);

-- Delete rows through a view
DELETE FROM view_name
WHERE condition;

```

**Notes:**

- Some DBMS (like SQL Server or Oracle) allow **INSTEAD OF triggers** to make **complex views updatable**.
- Updating a **non-updatable view** will cause an error.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Update a view|`UPDATE view_name SET col = val WHERE ...`|Must be updatable|
|Insert through view|`INSERT INTO view_name (col1, col2) VALUES (...);`|Must satisfy table constraints|
|Delete through view|`DELETE FROM view_name WHERE ...;`|Removes rows in base table|
|Non-updatable view|View with join, aggregation, or DISTINCT|Cannot update directly without triggers|
|INSTEAD OF trigger|Allows updates on complex views|DBMS-specific feature|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5000|
|2|Bob|IT|6000|

### Step 1: Create a simple updatable view

```SQL
CREATE VIEW hr_employees AS
SELECT employee_id, name, salary
FROM employees
WHERE department = 'HR';

```

---

### Step 2: Update through the view

```SQL
UPDATE hr_employees
SET salary = 5500
WHERE name = 'Alice';

```

✅ Changes reflected in **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5500|
|2|Bob|IT|6000|

---

### Step 3: Insert through the view

```SQL
INSERT INTO hr_employees (employee_id, name, salary)
VALUES (3, 'Carol', 5000);

```

✅ New row added to **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5500|
|2|Bob|IT|6000|
|3|Carol|HR|5000|

---

### Step 4: Delete through the view

```SQL
DELETE FROM hr_employees
WHERE name = 'Alice';

```

✅ Alice removed from **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|2|Bob|IT|6000|
|3|Carol|HR|5000|

---

## ✅ Key Takeaways

- **Updatable views** allow `INSERT`, `UPDATE`, and `DELETE` on underlying tables.
- Must meet **simple view criteria** (single table, no aggregates, no DISTINCT/UNION).
- Complex views can be made updatable using **INSTEAD OF triggers** (DBMS-specific).
- Provides **data abstraction, security, and reusability** while still allowing modifications.