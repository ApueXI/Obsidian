---
Created: 2025-09-09T20:03
tags:
  - Subqueries
---
## 1. Full Explanation

### 🔹 What is a Table Subquery?

- A **table subquery** (also called a **subquery in the FROM clause**) returns **one or more rows and columns**.
- Treated as a **temporary table** (derived table) that can be queried like a normal table.
- Useful for **aggregations, filtering, or transformations** before joining or selecting.

### 🔹 General Syntax

```SQL
SELECT t1.column1, t2.column2
FROM table1 t1
JOIN (SELECT column1, column2 FROM table2 WHERE condition) AS t2
ON t1.column1 = t2.column1;

```

**Notes:**

- Table subqueries must have an **alias**.
- Can be combined with **JOINs, WHERE, GROUP BY, and HAVING**.
- Returns **multiple rows and columns**, unlike scalar or row subqueries.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|FROM clause subquery|`FROM (SELECT col1, col2 FROM table2) AS t2`|Temporary table used in main query|
|JOIN with table subquery|`JOIN (SELECT col1, col2 ...) AS t2 ON t1.col1 = t2.col1`|Combine derived table with another table|
|Aggregate before join|`(SELECT dept, MAX(salary) AS max_salary FROM employees GROUP BY dept) AS t2`|Preprocess data|
|Alias required|`AS alias_name`|Mandatory for table subquery|
|Use in WHERE / HAVING|Can filter based on derived table|Flexible filtering|

---

## 3. Real-World Example

Suppose we have an **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|100000|
|2|Bob|IT|80000|
|3|Charlie|IT|90000|
|4|Dave|HR|70000|

### Step 1: Find max salary per department using table subquery

```SQL
SELECT e.name, e.salary, t.max_salary
FROM employees e
JOIN (
    SELECT department, MAX(salary) AS max_salary
    FROM employees
    GROUP BY department
) AS t
ON e.department = t.department
WHERE e.salary = t.max_salary;

```

✅ Returns employees with **max salary per department**:

|name|salary|max_salary|
|---|---|---|
|Alice|100000|100000|
|Charlie|90000|90000|

> Note: The subquery (SELECT department, MAX(salary)...) acts as a temporary table t.

### Step 2: Use table subquery in FROM for filtering

```SQL
SELECT t.department, COUNT(*) AS employee_count
FROM (
    SELECT *
    FROM employees
    WHERE salary > 80000
) AS t
GROUP BY t.department;

```

✅ Returns departments with employees earning **more than 80,000**:

|department|employee_count|
|---|---|
|HR|1|
|IT|1|

---

## ✅ Key Takeaways

- Table subqueries **return multiple rows and columns**.
- Used in **FROM clause** as a **derived table**.
- Must have an **alias**.
- Useful for **preprocessing, aggregation, or filtering** before joining or selecting.
- Complements scalar and row subqueries for **complex queries**.