---
Created: 2025-09-09T19:51
tags:
  - Sorting-&-Limiting
---
## 1. Full Explanation

### 🔹 What are `LIMIT` and `OFFSET`?

- `LIMIT` restricts the **number of rows returned** by a query.
- `OFFSET` skips a **specific number of rows** before returning results.
- Useful for **pagination** or retrieving only a subset of data.

### 🔹 `FETCH FIRST n ROWS`

- SQL standard alternative to `LIMIT`.
- Commonly used in **Oracle, DB2, SQL Server (with OFFSET)**.

---

### 🔹 General Syntax

**1. MySQL / PostgreSQL:**

```SQL
SELECT column1, column2
FROM table_name
ORDER BY column1
LIMIT n;                  -- Returns first n rows

SELECT column1, column2
FROM table_name
ORDER BY column1
LIMIT n OFFSET m;         -- Skips m rows, returns next n rows

```

**2. SQL Standard / Oracle / DB2:**

```SQL
SELECT column1, column2
FROM table_name
ORDER BY column1
OFFSET m ROWS FETCH FIRST n ROWS ONLY;

```

**Notes:**

- Always use `ORDER BY` to ensure **consistent results**.
- `LIMIT` and `OFFSET` are **0-based** in most databases.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Limit rows|`LIMIT 5`|Returns only first 5 rows|
|Offset rows|`LIMIT 5 OFFSET 10`|Skips 10 rows, returns next 5|
|SQL standard fetch|`OFFSET 10 ROWS FETCH FIRST 5 ROWS ONLY`|Same as LIMIT/OFFSET|
|Pagination (page 2 of 5 rows)|`LIMIT 5 OFFSET 5`|Skip first page, return second page|
|Combine with ORDER BY|`ORDER BY price DESC LIMIT 3`|Top 3 most expensive products|

---

## 3. Real-World Example

Suppose we have a **Products table**:

|product_id|name|price|category|
|---|---|---|---|
|1|Laptop|999.99|Electronics|
|2|Mouse|25.50|Electronics|
|3|Chair|75.00|Furniture|
|4|Desk|150.00|Furniture|
|5|Keyboard|49.99|Electronics|
|6|Monitor|199.99|Electronics|

### Step 1: Limit 3 rows

```SQL
SELECT name, price
FROM products
ORDER BY price DESC
LIMIT 3;

```

✅ Returns: Laptop, Monitor, Desk

### Step 2: Limit with offset

```SQL
SELECT name, price
FROM products
ORDER BY price DESC
LIMIT 3 OFFSET 3;

```

✅ Returns: Chair, Keyboard, Mouse (next 3 most expensive)

### Step 3: SQL standard syntax

```SQL
SELECT name, price
FROM products
ORDER BY price DESC
OFFSET 3 ROWS FETCH FIRST 3 ROWS ONLY;

```

✅ Same result as Step 2

---

## ✅ Key Takeaways

- `LIMIT` → restricts number of rows returned.
- `OFFSET` → skips rows for **pagination**.
- `FETCH FIRST n ROWS` → SQL standard alternative.
- Always use `ORDER BY` with `LIMIT/OFFSET` for **predictable results**.
- Essential for **paginated queries** in web applications.