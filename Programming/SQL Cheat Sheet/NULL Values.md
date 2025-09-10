---
Created: 2025-09-09T19:23
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 What is `NULL`?

- `NULL` = **no value / unknown / missing**.
- It does **not** mean `0`, an empty string (`''`), or `false`.
- Any column in a table can hold `NULL` unless it’s defined with `NOT NULL`.

### 🔹 Important Notes

- `NULL` is **not equal** to anything, even another `NULL`.
- Comparisons using `=` or `!=` won’t work. Instead, use:
    - `IS NULL`
    - `IS NOT NULL`

---

## 2. Summary Table (Quick Reference)

|**Concept**|**Example**|**Explanation**|
|---|---|---|
|Check for NULL|`WHERE email IS NULL`|Finds rows where email is missing|
|Check for NOT NULL|`WHERE email IS NOT NULL`|Finds rows with valid email|
|Insert NULL|`INSERT INTO users (id, name, email) VALUES (1, 'Alice', NULL);`|Email is missing|
|Aggregates ignore NULL|`SELECT AVG(score) FROM tests;`|Skips NULL values|
|Replace NULL|`SELECT COALESCE(email, 'No Email') FROM users;`|Substitutes NULL with default|
|Sort with NULL|`ORDER BY email NULLS LAST;` (Postgres)|Controls NULL position in sorting|

---

## 3. Real-World Example

Imagine a **Users table**:

```SQL
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

```

### Insert rows with NULL values:

```SQL
INSERT INTO users (user_id, name, email)
VALUES
(1, 'Alice', 'alice@email.com'),
(2, 'Bob', NULL),
(3, 'Charlie', 'charlie@email.com');

```

### Query 1: Find users without email

```SQL
SELECT name FROM users WHERE email IS NULL;

```

✅ Returns: `Bob`

### Query 2: Replace NULL with text

```SQL
SELECT name, COALESCE(email, 'No Email') AS contact
FROM users;

```

✅ Returns:

|name|contact|
|---|---|
|Alice|alice@email.com|
|Bob|No Email|
|Charlie|charlie@email.com|

---

## ✅ Key Takeaways

- `NULL` means **missing / unknown**, not zero or empty.
- Always use `IS NULL` or `IS NOT NULL` for checks.
- Aggregates (`COUNT`, `AVG`, etc.) **ignore** `NULL`.
- Use `COALESCE()` or `IFNULL()` to handle `NULL` gracefully.