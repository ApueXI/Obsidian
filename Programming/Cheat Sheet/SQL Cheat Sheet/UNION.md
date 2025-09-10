---
Created: 2025-09-09T20:09
tags:
  - Set-Operatoins
---
## 1. Full Explanation

### 🔹 What is `UNION`?

- `UNION` combines the results of **two or more** `**SELECT**` **queries** into a single result set.
- **Removes duplicate rows** automatically.
- All queries must return the **same number of columns** with **compatible data types**.

### 🔹 What is `UNION ALL`?

- `UNION ALL` also combines results but **includes duplicates**.
- Faster than `UNION` because no duplicate removal is performed.

### 🔹 General Syntax

```SQL
-- UNION (removes duplicates)
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;

-- UNION ALL (includes duplicates)
SELECT column1, column2 FROM table1
UNION ALL
SELECT column1, column2 FROM table2;

```

**Notes:**

- Column names in the final result are taken from the **first query**.
- Can include **ORDER BY** at the end of the final combined result.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Combine results (no duplicates)|`SELECT ... FROM t1 UNION SELECT ... FROM t2`|Removes duplicates|
|Combine results (all rows)|`UNION ALL`|Includes duplicates, faster|
|Column requirement|Same number & compatible types|Mandatory|
|ORDER BY combined result|`... UNION SELECT ... ORDER BY column`|Applies to entire union|
|Use for multiple tables|Can union more than 2 tables|Just stack UNION / UNION ALL|

---

## 3. Real-World Example

Suppose we have **Employees_US table**:

|employee_id|name|department|
|---|---|---|
|1|Alice|HR|
|2|Bob|IT|

**Employees_EU table**:

|employee_id|name|department|
|---|---|---|
|3|Charlie|IT|
|4|Bob|IT|

---

### Step 1: UNION (removes duplicates)

```SQL
SELECT name, department FROM Employees_US
UNION
SELECT name, department FROM Employees_EU;

```

✅ Returns unique employees:

|name|department|
|---|---|
|Alice|HR|
|Bob|IT|
|Charlie|IT|

> Note: Bob appears only once because duplicates are removed.

---

### Step 2: UNION ALL (includes duplicates)

```SQL
SELECT name, department FROM Employees_US
UNION ALL
SELECT name, department FROM Employees_EU;

```

✅ Returns all employees including duplicates:

|name|department|
|---|---|
|Alice|HR|
|Bob|IT|
|Charlie|IT|
|Bob|IT|

> Note: Bob appears twice because UNION ALL does not remove duplicates.

---

### Step 3: ORDER BY final result

```SQL
SELECT name, department FROM Employees_US
UNION
SELECT name, department FROM Employees_EU
ORDER BY name;

```

✅ Returns **sorted unique employees**:

|name|department|
|---|---|
|Alice|HR|
|Bob|IT|
|Charlie|IT|

---

## ✅ Key Takeaways

- `UNION` merges multiple queries **and removes duplicates**.
- `UNION ALL` merges multiple queries **and keeps duplicates**.
- All queries must have **same number of columns** with compatible types.
- Can combine multiple tables and use **ORDER BY** for final output.
- Use `UNION ALL` for **performance** when duplicates are acceptable.