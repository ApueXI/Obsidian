---
Created: 2025-09-09T20:09
tags:
  - Set-Operatoins
---
## 1. Full Explanation

### 🔹 What is `UNION ALL`?

- `UNION ALL` combines the results of **two or more** `**SELECT**` **queries** into a single result set.
- **Keeps all duplicate rows** (unlike `UNION`, which removes duplicates).
- Useful when you want **all data including repeated entries** and want **better performance**, as no duplicate checking is done.

### 🔹 General Syntax

```SQL
SELECT column1, column2 FROM table1
UNION ALL
SELECT column1, column2 FROM table2
UNION ALL
SELECT column1, column2 FROM table3;

```

**Notes:**

- All SELECT queries must return the **same number of columns** with **compatible data types**.
- Column names in the final result come from the **first SELECT query**.
- `ORDER BY` can be applied **at the end of the final combined result**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Combine results, keep duplicates|`SELECT ... FROM t1 UNION ALL SELECT ... FROM t2`|Duplicates are included|
|Column requirement|Same number & compatible types|Mandatory|
|Multiple tables|Stack multiple UNION ALL queries|Just keep adding UNION ALL|
|ORDER BY final result|`... UNION ALL ... ORDER BY column`|Sorts combined results|
|Performance|Faster than UNION|No duplicate removal|

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

### Step 1: Combine with `UNION ALL`

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

> Note: Bob appears twice, because duplicates are not removed.

---

### Step 2: Combine multiple tables

```SQL
SELECT name, department FROM Employees_US
UNION ALL
SELECT name, department FROM Employees_EU
UNION ALL
SELECT name, department FROM Employees_Asia;

```

✅ All rows from all three tables are combined **without removing duplicates**.

---

### Step 3: ORDER BY final result

```SQL
SELECT name, department FROM Employees_US
UNION ALL
SELECT name, department FROM Employees_EU
ORDER BY name;

```

✅ Returns **sorted combined results** including duplicates:

|name|department|
|---|---|
|Alice|HR|
|Bob|IT|
|Bob|IT|
|Charlie|IT|

---

## ✅ Key Takeaways

- `UNION ALL` combines multiple SELECT queries **and keeps all duplicates**.
- **Faster than** `**UNION**` because no duplicate checking is performed.
- Must have **same number of columns** with compatible data types.
- Column names come from the **first SELECT query**.
- Useful for **stacking multiple datasets** where duplicates are allowed or expected.