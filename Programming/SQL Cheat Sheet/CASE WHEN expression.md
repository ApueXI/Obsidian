---
Created: 2025-09-09T20:21
tags:
  - Advance-Querying
---
## 1. Full Explanation

### 🔹 What is `CASE WHEN`?

- `CASE WHEN` is **SQL’s conditional expression**, similar to **if-else statements** in programming.
- Allows you to **return different values** based on conditions.
- Can be used in **SELECT, UPDATE, ORDER BY, and WHERE clauses**.

---

### 🔹 General Syntax

**Simple CASE** (compares a column/expression to values):

```SQL
SELECT column,
       CASE column
           WHEN value1 THEN result1
           WHEN value2 THEN result2
           ELSE default_result
       END AS alias_name
FROM table_name;

```

**Searched CASE** (uses boolean conditions):

```SQL
SELECT column,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE default_result
       END AS alias_name
FROM table_name;

```

**Notes:**

- `ELSE` is optional; if omitted, unmatched rows return `NULL`.
- Can be used in **aggregation, ordering, and filtering**.

---

## 2. Summary Table (Quick Reference)

|Feature|Syntax / Example|Notes|
|---|---|---|
|Simple CASE|`CASE col WHEN 1 THEN 'One' ELSE 'Other' END`|Compares a column to values|
|Searched CASE|`CASE WHEN col>10 THEN 'High' ELSE 'Low' END`|Uses boolean conditions|
|Alias name|`AS alias_name`|Required to name result column|
|Use in SELECT|`SELECT CASE ... END FROM table`|Most common usage|
|Use in UPDATE|`UPDATE table SET col = CASE ... END`|Conditional updates|
|Use in ORDER BY|`ORDER BY CASE ... END`|Conditional sorting|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|salary|
|---|---|---|
|1|Alice|5000|
|2|Bob|6000|
|3|Charlie|4000|

### Step 1: Categorize salaries

```SQL
SELECT name, salary,
       CASE
           WHEN salary >= 5500 THEN 'High'
           WHEN salary >= 4500 THEN 'Medium'
           ELSE 'Low'
       END AS salary_level
FROM employees;

```

✅ Returns:

|name|salary|salary_level|
|---|---|---|
|Alice|5000|Medium|
|Bob|6000|High|
|Charlie|4000|Low|

---

### Step 2: Use in UPDATE

```SQL
UPDATE employees
SET salary_level = CASE
                       WHEN salary >= 5500 THEN 'High'
                       WHEN salary >= 4500 THEN 'Medium'
                       ELSE 'Low'
                   END;

```

✅ Updates a column `salary_level` in the table based on conditions.

---

### Step 3: Use in ORDER BY

```SQL
SELECT name, salary
FROM employees
ORDER BY CASE
             WHEN salary >= 5500 THEN 1
             WHEN salary >= 4500 THEN 2
             ELSE 3
         END;

```

✅ Rows sorted **High → Medium → Low** salary categories.

---

## ✅ Key Takeaways

- `CASE WHEN` allows **conditional logic** in SQL queries.
- Can be **simple** (compare column to values) or **searched** (boolean conditions).
- Works in **SELECT, UPDATE, ORDER BY, and WHERE** clauses.
- `ELSE` is optional; missing it returns **NULL** for unmatched cases.
- Essential for **dynamic categorization, conditional updates, and sorting**.