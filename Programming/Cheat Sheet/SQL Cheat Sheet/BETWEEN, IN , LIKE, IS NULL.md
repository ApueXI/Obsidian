---
Created: 2025-09-09T19:49
tags:
  - Basic-Queries-(SELECT)
---
## 1. Full Explanation

### 🔹 `BETWEEN`

- Filters values **within a range** (inclusive).
- Works with **numbers, dates, and text**.

```SQL
SELECT * FROM products
WHERE price BETWEEN 50 AND 150;

```

✅ Returns rows where price ≥ 50 and ≤ 150.

---

### 🔹 `IN`

- Checks if a value **matches any value in a list**.
- Shortcut for multiple OR conditions.

```SQL
SELECT * FROM users
WHERE status IN ('active', 'pending');

```

✅ Returns users whose status is either active or pending.

---

### 🔹 `LIKE`

- Matches values based on **patterns**.
- Wildcards:
    - `%` → any sequence of characters
    - `_` → any single character

```SQL
SELECT * FROM users
WHERE name LIKE 'A%';   -- Names starting with 'A'

SELECT * FROM users
WHERE name LIKE '_ve';  -- Names with 've' as last two letters

```

---

### 🔹 `IS NULL` / `IS NOT NULL`

- Checks for **missing values**.
- Cannot use `=` or `!=` with NULL.

```SQL
SELECT * FROM users
WHERE email IS NULL;       -- Missing email

SELECT * FROM users
WHERE email IS NOT NULL;   -- Email exists

```

---

## 2. Summary Table (Quick Reference)

|Operator|Description|Example|
|---|---|---|
|`BETWEEN`|Values within a range|`price BETWEEN 50 AND 150`|
|`IN`|Value matches a list|`status IN ('active','pending')`|
|`LIKE`|Pattern matching|`name LIKE 'A%'`|
|`IS NULL`|Checks for missing values|`email IS NULL`|
|`IS NOT NULL`|Checks for non-missing values|`email IS NOT NULL`|

---

## 3. Real-World Example

Suppose we have a **Users table**:

|user_id|name|age|status|email|
|---|---|---|---|---|
|1|Alice|25|active|alice@email.com|
|2|Bob|17|inactive|NULL|
|3|Charlie|30|pending|charlie@email.com|
|4|Dave|22|active|NULL|
|5|Eve|28|inactive|eve@email.com|

### Step 1: Using BETWEEN

```SQL
SELECT name, age
FROM users
WHERE age BETWEEN 20 AND 30;

```

✅ Returns: Alice, Charlie, Dave, Eve

### Step 2: Using IN

```SQL
SELECT name, status
FROM users
WHERE status IN ('active', 'pending');

```

✅ Returns: Alice, Charlie, Dave

### Step 3: Using LIKE

```SQL
SELECT name
FROM users
WHERE name LIKE 'A%';

```

✅ Returns: Alice

### Step 4: Using IS NULL

```SQL
SELECT name
FROM users
WHERE email IS NULL;

```

✅ Returns: Bob, Dave

### Step 5: Using IS NOT NULL

```SQL
SELECT name
FROM users
WHERE email IS NOT NULL;

```

✅ Returns: Alice, Charlie, Eve

---

## ✅ Key Takeaways

- `BETWEEN` → Range check (inclusive).
- `IN` → Matches any value from a list.
- `LIKE` → Pattern matching using `%` and `_`.
- `IS NULL` / `IS NOT NULL` → Detect missing or existing values.
- Often combined with **WHERE** and **logical operators** (`AND`, `OR`, `NOT`).