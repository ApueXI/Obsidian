---
Created: 2025-09-09T19:48
tags:
  - Basic-Queries-(SELECT)
---
## 1. Full Explanation

### 🔹 What is `WHERE`?

- `WHERE` is used in **SELECT, UPDATE, DELETE** queries.
- It **filters rows** based on conditions.
- Only rows that **meet the condition** are returned, updated, or deleted.

### 🔹 Comparison Operators

|Operator|Description|Example|
|---|---|---|
|`=`|Equal to|`WHERE age = 25`|
|`<>` or `!=`|Not equal to|`WHERE status <> 'active'`|
|`>`|Greater than|`WHERE price > 100`|
|`<`|Less than|`WHERE price < 50`|
|`>=`|Greater than or equal to|`WHERE age >= 18`|
|`<=`|Less than or equal to|`WHERE age <= 65`|

---

### 🔹 Logical Operators

|Operator|Description|Example|
|---|---|---|
|`AND`|Both conditions must be true|`WHERE age > 18 AND status='active'`|
|`OR`|Either condition is true|`WHERE status='active' OR status='pending'`|
|`NOT`|Negates a condition|`WHERE NOT status='inactive'`|

---

### 🔹 Special Operators

|Operator|Description|Example|
|---|---|---|
|`BETWEEN`|Between a range (inclusive)|`WHERE price BETWEEN 50 AND 100`|
|`IN`|Matches any value in a list|`WHERE status IN ('active', 'pending')`|
|`LIKE`|Pattern matching (`%`, `_`)|`WHERE name LIKE 'A%'` (names starting with A)|
|`IS NULL`|Checks for NULL values|`WHERE email IS NULL`|
|`IS NOT NULL`|Checks for non-NULL values|`WHERE email IS NOT NULL`|

---

## 2. Real-World Example

Suppose we have a **Products table**:

|product_id|name|price|category|stock|
|---|---|---|---|---|
|1|Laptop|999.99|Electronics|50|
|2|Mouse|25.50|Electronics|200|
|3|Chair|75.00|Furniture|100|
|4|Desk|150.00|Furniture|20|

### Step 1: Filter with comparison

```SQL
SELECT name, price
FROM products
WHERE price > 100;

```

✅ Returns: Laptop, Desk

### Step 2: Filter with AND

```SQL
SELECT name, price
FROM products
WHERE price > 50 AND category = 'Electronics';

```

✅ Returns: Laptop

### Step 3: Filter with OR

```SQL
SELECT name, price
FROM products
WHERE category = 'Electronics' OR stock < 50;

```

✅ Returns: Laptop, Mouse, Desk

### Step 4: Filter with BETWEEN

```SQL
SELECT name, price
FROM products
WHERE price BETWEEN 50 AND 150;

```

✅ Returns: Chair, Desk

### Step 5: Filter with IN

```SQL
SELECT name, category
FROM products
WHERE category IN ('Electronics', 'Furniture');

```

✅ Returns all rows

### Step 6: Filter with LIKE

```SQL
SELECT name
FROM products
WHERE name LIKE 'D%';

```

✅ Returns: Desk

---

## ✅ Key Takeaways

- `WHERE` **filters rows** based on conditions.
- Supports **comparison**, **logical**, and **special operators**.
- Use `AND`, `OR`, `NOT` to combine conditions.
- `LIKE` and `IN` help match **patterns or lists**.
- `IS NULL` / `IS NOT NULL` handle missing data.