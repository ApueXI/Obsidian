---
Created: 2025-09-09T20:02
tags:
  - Subqueries
---
## 1. Full Explanation

### 🔹 What is a Scalar Subquery?

- A **scalar subquery** is a **subquery that returns exactly one value** (one row, one column).
- Can be used anywhere a **single value** is expected: in `SELECT`, `WHERE`, or `HAVING` clauses.
- If the subquery returns **more than one value**, it causes an error.

### 🔹 General Syntax

**1. In SELECT clause:**

```SQL
SELECT column1,
       (SELECT aggregate_column FROM table2 WHERE condition) AS alias_name
FROM table1;

```

**2. In WHERE clause:**

```SQL
SELECT column1
FROM table1
WHERE column2 = (SELECT aggregate_column FROM table2 WHERE condition);

```

**3. In HAVING clause:**

```SQL
SELECT column1, COUNT(*)
FROM table1
GROUP BY column1
HAVING COUNT(*) > (SELECT AVG(column2) FROM table2);

```

**Notes:**

- Returns a **single scalar value**.
- Can be used for **comparison, calculation, or assignment** in queries.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|SELECT with scalar subquery|`(SELECT MAX(price) FROM products)`|Returns single value|
|WHERE with scalar subquery|`WHERE salary > (SELECT AVG(salary) FROM employees)`|Filter rows by a single value|
|HAVING with scalar subquery|`HAVING COUNT(*) > (SELECT AVG(count) FROM table)`|Filter groups by a single value|
|Must return single value|One row, one column|Otherwise error occurs|
|Alias optional|`AS alias_name`|Makes output readable|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|100000|
|2|Bob|IT|80000|
|3|Charlie|IT|90000|
|4|Dave|HR|70000|

### Step 1: Scalar subquery in SELECT

```SQL
SELECT name,
       salary,
       (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;

```

✅ Returns each employee’s salary **and overall average salary**:

|name|salary|avg_salary|
|---|---|---|
|Alice|100000|85000|
|Bob|80000|85000|
|Charlie|90000|85000|
|Dave|70000|85000|

---

### Step 2: Scalar subquery in WHERE

```SQL
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

```

✅ Returns employees earning **above average salary**:

|name|salary|
|---|---|
|Alice|100000|
|Charlie|90000|

---

### Step 3: Scalar subquery in HAVING

```SQL
SELECT department, COUNT(*) AS emp_count
FROM employees
GROUP BY department
HAVING COUNT(*) > (SELECT AVG(emp_count) FROM (SELECT department, COUNT(*) AS emp_count FROM employees GROUP BY department) AS dept_counts);

```

✅ Returns departments with **more employees than the average** (complex example).

---

## ✅ Key Takeaways

- Scalar subqueries **return a single value**.
- Can be used in **SELECT, WHERE, or HAVING**.
- Must **not return multiple rows or columns**.
- Very useful for **comparisons, calculations, or embedding aggregate results**.