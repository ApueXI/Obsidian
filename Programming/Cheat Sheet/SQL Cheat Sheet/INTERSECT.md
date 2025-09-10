---
Created: 2025-09-09T20:09
tags:
  - Set-Operatoins
---
## 1. Full Explanation

### 🔹 What is `INTERSECT`?

- `INTERSECT` returns **only the rows that are common to two or more** `**SELECT**` **queries**.
- Automatically **removes duplicates** in the final result.
- All SELECT queries must return the **same number of columns** with **compatible data types**.
- Useful for finding **common elements between datasets**.

### 🔹 General Syntax

```SQL
SELECT column1, column2 FROM table1
INTERSECT
SELECT column1, column2 FROM table2;

```

**Notes:**

- Column names in the result are taken from the **first SELECT query**.
- Some databases (like MySQL) **do not support INTERSECT** directly; use `INNER JOIN` as an alternative.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Find common rows|`SELECT ... FROM t1 INTERSECT SELECT ... FROM t2`|Only rows present in both queries|
|Removes duplicates automatically|Yes|Unlike UNION ALL|
|Column requirement|Same number & compatible types|Mandatory|
|ORDER BY final result|`... INTERSECT ... ORDER BY column`|Sort combined results|
|Alternative in MySQL|`INNER JOIN` on multiple columns|Simulates INTERSECT|

---

## 3. Real-World Example

Suppose we have **Employees_US table**:

|employee_id|name|department|
|---|---|---|
|1|Alice|HR|
|2|Bob|IT|
|3|Charlie|IT|

**Employees_EU table**:

|employee_id|name|department|
|---|---|---|
|2|Bob|IT|
|3|Charlie|IT|
|4|David|Sales|

---

### Step 1: Find employees in **both US and EU tables**

```SQL
SELECT name, department FROM Employees_US
INTERSECT
SELECT name, department FROM Employees_EU;

```

✅ Returns rows **common to both tables**:

|name|department|
|---|---|
|Bob|IT|
|Charlie|IT|

> Note: Alice (US only) and David (EU only) are excluded.

---

### Step 2: Combine with ORDER BY

```SQL
SELECT name, department FROM Employees_US
INTERSECT
SELECT name, department FROM Employees_EU
ORDER BY name;

```

✅ Returns sorted common employees:

|name|department|
|---|---|
|Bob|IT|
|Charlie|IT|

---

## ✅ Key Takeaways

- `INTERSECT` returns **only rows present in all SELECT queries**.
- Automatically **removes duplicates**.
- All queries must have **same number of columns** with compatible types.
- Useful for **finding overlaps, shared data, or common records**.
- Alternative in MySQL: use **INNER JOIN** with multiple columns.