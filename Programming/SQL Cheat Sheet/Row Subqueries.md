---
Created: 2025-09-09T20:02
tags:
  - Subqueries
---
## 1. Full Explanation

### 🔹 What is a Row Subquery?

- A **row subquery** returns **one or more columns but only a single row**.
- Can be used in **WHERE, HAVING, or FROM** clauses.
- Unlike scalar subqueries (1 value), **row subqueries return a tuple** of values.
- Useful for comparing **multiple columns at once**.

### 🔹 General Syntax

**1. In WHERE clause:**

```SQL
SELECT *
FROM table1
WHERE (column1, column2) =
      (SELECT column1, column2
       FROM table2
       WHERE condition);

```

**2. In FROM clause (as derived table):**

```SQL
SELECT t1.*
FROM table1 t1
JOIN (SELECT column1, column2 FROM table2 WHERE condition) t2
ON t1.column1 = t2.column1;

```

**Notes:**

- Must return **exactly one row**; otherwise, it can cause errors.
- Can return **multiple columns**, unlike scalar subqueries.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|WHERE with row subquery|`(col1, col2) = (SELECT col1, col2 FROM table2 WHERE id=1)`|Compare multiple columns|
|FROM with row subquery|`JOIN (SELECT col1, col2 FROM table2 WHERE ...) AS t2`|Use subquery as a derived table|
|Must return single row|One row, multiple columns|Otherwise error occurs|
|Compare tuples|`(col1, col2) > (SELECT col1, col2 FROM ...)`|Tuple comparison supported|
|Often combined with JOIN|`INNER JOIN (row subquery)`|Simplifies complex queries|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|100000|
|2|Bob|IT|80000|
|3|Charlie|IT|90000|
|4|Dave|HR|70000|

**Departments table**:

|department|min_salary|max_salary|
|---|---|---|
|HR|70000|120000|
|IT|80000|95000|

### Step 1: Compare multiple columns with row subquery

```SQL
SELECT *
FROM employees e
WHERE (e.department, e.salary) =
      (SELECT d.department, d.max_salary
       FROM departments d
       WHERE d.department = e.department);

```

✅ Returns employees whose salary equals **the max salary in their department**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|100000|
|3|Charlie|IT|90000|

> Note: The row subquery returns a tuple (department, max_salary) for comparison.

### Step 2: Row subquery in FROM clause (derived table)

```SQL
SELECT e.name, e.salary, d.max_salary
FROM employees e
JOIN (SELECT department, max_salary FROM departments) d
ON e.department = d.department
WHERE e.salary = d.max_salary;

```

✅ Same result as Step 1 using **join with row subquery**.

---

## ✅ Key Takeaways

- Row subqueries **return a single row with multiple columns**.
- Can be used in **WHERE, HAVING, or FROM** clauses.
- Useful for **tuple comparisons** and complex filtering.
- Requires careful design to **ensure only one row is returned**.
- Often used in combination with **JOINs or scalar subqueries**.