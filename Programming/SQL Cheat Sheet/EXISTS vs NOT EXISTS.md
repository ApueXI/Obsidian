---
Created: 2025-09-09T20:04
tags:
  - Subqueries
---
## 1. Full Explanation

### 🔹 What is `EXISTS`?

- `EXISTS` checks if a **subquery returns at least one row**.
- Returns **TRUE** if the subquery has **any row**, otherwise **FALSE**.
- Often used in `WHERE` clauses to **filter based on the existence of related data**.

### 🔹 What is `NOT EXISTS`?

- `NOT EXISTS` is the opposite: returns **TRUE** if the subquery returns **no rows**.
- Useful for **excluding rows that have related records**.

### 🔹 General Syntax

```SQL
-- EXISTS
SELECT column1, column2
FROM table1
WHERE EXISTS (
    SELECT 1
    FROM table2
    WHERE table2.column = table1.column
);

-- NOT EXISTS
SELECT column1, column2
FROM table1
WHERE NOT EXISTS (
    SELECT 1
    FROM table2
    WHERE table2.column = table1.column
);

```

**Notes:**

- `SELECT 1` or `SELECT *` in subquery is standard; **the selected column doesn’t matter**, only row existence counts.
- Typically more efficient than `IN` for **large tables with indexes**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|EXISTS|`WHERE EXISTS (SELECT 1 FROM table2 WHERE ...)`|True if subquery returns ≥1 row|
|NOT EXISTS|`WHERE NOT EXISTS (SELECT 1 FROM table2 WHERE ...)`|True if subquery returns 0 rows|
|Can be correlated subquery|`table2.column = table1.column`|Subquery depends on outer query row|
|Efficient for large datasets|Often faster than IN|Especially with indexes|
|Can replace IN/NOT IN|Functional alternative|More readable for complex queries|

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
|Finance|Frank|

---

### Step 1: Find employees in departments that exist in Departments table

```SQL
SELECT name, department
FROM employees e
WHERE EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.department = e.department
);

```

✅ Returns employees whose **department exists**:

|name|department|
|---|---|
|Alice|HR|
|Bob|IT|
|Charlie|IT|
|Dave|HR|

> Eve (Sales) is excluded because Sales department is not in Departments table.

---

### Step 2: Find employees **not in any existing department**

```SQL
SELECT name, department
FROM employees e
WHERE NOT EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.department = e.department
);

```

✅ Returns employees whose department **does not exist in Departments table**:

|name|department|
|---|---|
|Eve|Sales|

---

## ✅ Key Takeaways

- `EXISTS` checks for **presence of rows** in a subquery; `NOT EXISTS` checks for **absence**.
- Subquery **can be correlated** with outer query for row-by-row checks.
- More **efficient than IN** for large datasets.
- Essential for **relational integrity checks, conditional filtering, and anti-joins**.