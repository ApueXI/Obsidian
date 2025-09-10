---
Created: 2025-09-09T19:48
tags:
  - Basic-Queries-(SELECT)
---
## 1. Full Explanation

### 🔹 What is `DISTINCT`?

- `DISTINCT` is a **keyword used in SELECT queries**.
- It **removes duplicate values** from the result set.
- Useful when you want **unique values** only.

### 🔹 General Syntax

```SQL
SELECT DISTINCT column1, column2, ...
FROM table_name;

```

**Notes:**

- `DISTINCT` applies to **all columns listed**.
- If multiple columns are listed, the combination of values must be unique.

---

## 2. Summary Table (Quick Reference)

|**Operation**|**Syntax / Example**|**Notes**|
|---|---|---|
|Select distinct single column|`SELECT DISTINCT status FROM users;`|Removes duplicate statuses|
|Select distinct multiple columns|`SELECT DISTINCT name, status FROM users;`|Combination of columns must be unique|
|With WHERE clause|`SELECT DISTINCT status FROM users WHERE status='active';`|Filters first, then applies DISTINCT|
|With ORDER BY|`SELECT DISTINCT status FROM users ORDER BY status ASC;`|Sorts unique values|
|Count distinct|`SELECT COUNT(DISTINCT status) FROM users;`|Counts unique values|

---

## 3. Real-World Example

Suppose we have a **Users table**:

|user_id|name|email|status|
|---|---|---|---|
|1|Alice|alice@email.com|active|
|2|Bob|bob@email.com|inactive|
|3|Charlie|charlie@email.com|active|
|4|Dave|dave@email.com|inactive|
|5|Eve|eve@email.com|active|

### Step 1: Select distinct single column

```SQL
SELECT DISTINCT status
FROM users;

```

✅ Returns:

status

---

active

---

inactive

---

### Step 2: Select distinct combination of columns

```SQL
SELECT DISTINCT status, name
FROM users;

```

✅ Returns unique **status + name** combinations.

### Step 3: Count distinct values

```SQL
SELECT COUNT(DISTINCT status) AS unique_statuses
FROM users;

```

✅ Returns: `2`

---

## ✅ Key Takeaways

- `DISTINCT` **removes duplicates** in query results.
- Works on **single or multiple columns**.
- Often combined with **COUNT** to get the number of unique values.
- Useful for **reporting, analytics, and cleaning duplicate data**.