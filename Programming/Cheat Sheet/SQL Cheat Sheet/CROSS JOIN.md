---
Created: 2025-09-09T19:55
tags:
  - Joins
---
## 1. Full Explanation

### 🔹 What is `CROSS JOIN`?

- `CROSS JOIN` returns the **Cartesian product** of two tables.
- Every row from the **first table** is combined with **every row from the second table**.
- Does **not require a matching condition** (`ON` clause).
- Useful for **generating all possible combinations**.

### 🔹 General Syntax

```SQL
SELECT table1.column1, table2.column2
FROM table1
CROSS JOIN table2;

```

**Notes:**

- Can produce **very large result sets** if both tables are large.
- Often used for **combinatorial problems**, **reporting**, or **test data generation**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic CROSS JOIN|`FROM table1 CROSS JOIN table2`|Cartesian product of both tables|
|Select specific columns|`SELECT t1.name, t2.color`|Choose which columns to display|
|Alias for tables|`FROM table1 t1 CROSS JOIN table2 t2`|Shorter references|
|Combine with WHERE|`WHERE t1.id <> t2.id`|Can filter combinations|
|No ON clause required|`CROSS JOIN` does not use matching column|Unlike INNER/OUTER JOIN|

---

## 3. Real-World Example

Suppose we have **two tables**:

**Products table**

|product_id|name|
|---|---|
|1|Laptop|
|2|Mouse|

**Colors table**

|color_id|color|
|---|---|
|1|Black|
|2|White|

### Step 1: Basic CROSS JOIN

```SQL
SELECT p.name, c.color
FROM products p
CROSS JOIN colors c;

```

✅ Returns:

|name|color|
|---|---|
|Laptop|Black|
|Laptop|White|
|Mouse|Black|
|Mouse|White|

> Note: Every product is combined with every color.

### Step 2: Using aliases

```SQL
SELECT p.name, c.color
FROM products AS p
CROSS JOIN colors AS c;

```

✅ Same result with shorter references.

### Step 3: Filter combinations with WHERE

```SQL
SELECT p.name, c.color
FROM products p
CROSS JOIN colors c
WHERE c.color <> 'White';

```

✅ Returns:

|name|color|
|---|---|
|Laptop|Black|
|Mouse|Black|

> Note: Filters out combinations where color is White.

---

## ✅ Key Takeaways

- `CROSS JOIN` produces a **Cartesian product** of two tables.
- Does **not require a matching column**.
- Can generate **all possible combinations** of rows.
- Be careful with large tables; the result grows **multiplicatively**.
- Often combined with `WHERE` to filter specific combinations.