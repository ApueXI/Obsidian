---
Created: 2025-09-09T20:14
tags:
  - Views
---
## 1. Full Explanation

### 🔹 What is a View?

- A **view** is a **virtual table** based on the result of a `SELECT` query.
- Does **not store data physically** (except **materialized views** in some DBMS).
- Provides a **simplified, reusable, and secure way** to access data.
- Can be used for **filtering, joining, aggregating, or hiding sensitive columns**.

---

### 🔹 General Syntax

```SQL
-- Basic View
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;

-- Example with JOIN
CREATE VIEW employee_summary AS
SELECT e.name, e.department, d.manager
FROM employees e
JOIN departments d ON e.department = d.department;

```

**Notes:**

- Column names in the view can be **renamed using AS**.
- Views **cannot always be updated** (depends on DBMS and complexity of SELECT).
- Use `DROP VIEW view_name;` to remove a view.

---

### 🔹 Advantages of Views

1. **Simplification** – hide complex queries from users.
2. **Security** – restrict access to specific columns or rows.
3. **Reusability** – can reuse queries multiple times.
4. **Consistency** – present a unified interface for complex joins or aggregations.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create a view|`CREATE VIEW view_name AS SELECT ...`|Virtual table, no data stored physically|
|Select from a view|`SELECT * FROM view_name;`|Works like a regular table|
|Updateable view|Depends on DBMS and SELECT complexity|Simple SELECTs usually updatable|
|Drop a view|`DROP VIEW view_name;`|Removes the view definition|
|Use joins in views|`CREATE VIEW v AS SELECT ... JOIN ...`|Simplifies repeated complex joins|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5000|
|2|Bob|IT|6000|
|3|Charlie|IT|5500|

**Departments table**:

|department|manager|
|---|---|
|HR|Alice|
|IT|Charlie|

---

### Step 1: Create a view for employee summary

```SQL
CREATE VIEW employee_summary AS
SELECT e.name, e.department, d.manager
FROM employees e
JOIN departments d ON e.department = d.department;

```

### Step 2: Query the view

```SQL
SELECT * FROM employee_summary;

```

✅ Returns:

|name|department|manager|
|---|---|---|
|Alice|HR|Alice|
|Bob|IT|Charlie|
|Charlie|IT|Charlie|

---

### Step 3: Create a view with filtering

```SQL
CREATE VIEW it_employees AS
SELECT name, salary
FROM employees
WHERE department = 'IT';

```

✅ Querying:

```SQL
SELECT * FROM it_employees;

```

|name|salary|
|---|---|
|Bob|6000|
|Charlie|5500|

---

## ✅ Key Takeaways

- Views are **virtual tables** that simplify and secure access to data.
- Can include **filters, joins, and aggregations**.
- **Does not store data physically** (except materialized views).
- Helps with **reusability, consistency, and security**.
- Can be queried like normal tables using `SELECT * FROM view_name`.