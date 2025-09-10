---
Created: 2025-09-09T20:03
tags:
  - Subqueries
---
## 1. Full Explanation

### 🔹 What is `IN` with Subqueries?

- The `IN` operator checks if a value **exists in a list of values**.
- When combined with a **subquery**, it checks if a value exists in the **result set returned by the subquery**.
- Often used in `WHERE` clauses for filtering.

### 🔹 General Syntax

```SQL
SELECT column1, column2
FROM table1
WHERE column1 IN (
    SELECT column1
    FROM table2
    WHERE condition
);

```

**Notes:**

- Subquery can return **one or multiple rows**.
- Equivalent to multiple OR conditions.
- Often used for **filtering based on related table data**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic IN with subquery|`WHERE column1 IN (SELECT column1 FROM table2)`|Filters rows if value exists in subquery results|
|Works with multiple values|Subquery can return multiple rows|No error if multiple rows|
|Can combine with NOT|`WHERE column1 NOT IN (SELECT ...)`|Excludes values in subquery|
|Often used with foreign keys|Filter related table records|Common in relational databases|
|Can use aggregate in subquery|`IN (SELECT MAX(column1) FROM table2)`|Works if single value returned|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|
|---|---|---|
|1|Alice|HR|
|2|Bob|IT|
|3|Charlie|IT|
|4|Dave|HR|
|5|Eve|Sales|

**Departments table**:

|department|manager|
|---|---|
|HR|Alice|
|IT|Charlie|
|Sales|Frank|

### Step 1: Find employees in departments with managers

```SQL
SELECT name, department
FROM employees
WHERE department IN (
    SELECT department
    FROM departments
);

```

✅ Returns all employees, because all their departments exist in Departments table:

|name|department|
|---|---|
|Alice|HR|
|Bob|IT|
|Charlie|IT|
|Dave|HR|
|Eve|Sales|

---

### Step 2: Find employees in departments with manager ‘Alice’

```SQL
SELECT name, department
FROM employees
WHERE department IN (
    SELECT department
    FROM departments
    WHERE manager = 'Alice'
);

```

✅ Returns employees in **HR department**:

|name|department|
|---|---|
|Alice|HR|
|Dave|HR|

---

### Step 3: Use NOT IN to exclude employees in IT

```SQL
SELECT name, department
FROM employees
WHERE department NOT IN (
    SELECT department
    FROM departments
    WHERE department = 'IT'
);

```

✅ Returns employees **not in IT department**:

|name|department|
|---|---|
|Alice|HR|
|Dave|HR|
|Eve|Sales|

---

## ✅ Key Takeaways

- `IN` with subqueries **filters rows based on another table or query result**.
- Can handle **multiple values** from subquery.
- `NOT IN` excludes matching values.
- Often used for **foreign key filtering or conditional selection**.
- Simpler alternative to multiple OR conditions.