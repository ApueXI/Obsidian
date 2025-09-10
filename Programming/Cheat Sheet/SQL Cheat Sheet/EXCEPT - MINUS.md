---
Created: 2025-09-09T20:09
tags:
  - Set-Operatoins
---
## 1. Full Explanation

### 🔹 What is `EXCEPT` / `MINUS`?

- `EXCEPT` (in SQL Server, PostgreSQL) or `MINUS` (in Oracle) returns **rows from the first query that are not present in the second query**.
- Automatically **removes duplicates** in the final result.
- All SELECT queries must return the **same number of columns** with **compatible data types**.
- Useful for finding **differences between datasets**.

### 🔹 General Syntax

```SQL
-- EXCEPT (SQL Server, PostgreSQL)
SELECT column1, column2 FROM table1
EXCEPT
SELECT column1, column2 FROM table2;

-- MINUS (Oracle)
SELECT column1, column2 FROM table1
MINUS
SELECT column1, column2 FROM table2;

```

**Notes:**

- Column names in the result come from the **first SELECT query**.
- Some databases (like MySQL) **do not support EXCEPT/MINUS** directly; use **LEFT JOIN with WHERE IS NULL** as an alternative.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Find rows in first query only|`SELECT ... FROM t1 EXCEPT SELECT ... FROM t2`|Returns only rows not in second query|
|Removes duplicates automatically|Yes|Like INTERSECT and UNION|
|Column requirement|Same number & compatible types|Mandatory|
|Alternative in MySQL|`LEFT JOIN ... WHERE t2.col IS NULL`|Simulates EXCEPT/MINUS|
|ORDER BY final result|`... EXCEPT ... ORDER BY column`|Sort combined results|

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

### Step 1: Find employees **only in US**

```SQL
SELECT name, department FROM Employees_US
EXCEPT
SELECT name, department FROM Employees_EU;

```

✅ Returns employees in **US table but not EU table**:

|name|department|
|---|---|
|Alice|HR|

> Note: Bob and Charlie exist in both → excluded.

---

### Step 2: Find employees **only in EU** (reverse)

```SQL
SELECT name, department FROM Employees_EU
EXCEPT
SELECT name, department FROM Employees_US;

```

✅ Returns employees in **EU table but not US table**:

|name|department|
|---|---|
|David|Sales|

---

### Step 3: Combine with ORDER BY

```SQL
SELECT name, department FROM Employees_US
EXCEPT
SELECT name, department FROM Employees_EU
ORDER BY name;

```

✅ Returns sorted result of employees **only in US**:

|name|department|
|---|---|
|Alice|HR|

---

## ✅ Key Takeaways

- `EXCEPT` / `MINUS` returns **rows in the first query not in the second query**.
- Automatically **removes duplicates**.
- Requires **same number of columns** with compatible types.
- Useful for **finding differences, unmatched records, or “anti-joins”**.
- MySQL alternative: **LEFT JOIN with IS NULL**.