---
Created: 2025-09-09T19:50
tags:
  - Sorting-&-Limiting
---
## 1. Full Explanation

### 🔹 What is `ORDER BY`?

- `ORDER BY` is used in **SELECT queries** to **sort the result set**.
- You can sort **ascending (**`**ASC**`**)** or **descending (**`**DESC**`**)**.
- By default, `ORDER BY` sorts **ascending**.

### 🔹 General Syntax

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;

```

**Notes:**

- Can sort by **one or multiple columns**.
- Often combined with **WHERE**, **LIMIT**, or **DISTINCT**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Sort ascending (default)|`ORDER BY price ASC`|Smallest → Largest|
|Sort descending|`ORDER BY price DESC`|Largest → Smallest|
|Sort by multiple columns|`ORDER BY category ASC, price DESC`|Sort first by category, then by price|
|With WHERE filter|`SELECT * FROM products WHERE stock > 0 ORDER BY price DESC;`|Filters then sorts|
|With LIMIT (top N rows)|`ORDER BY price DESC LIMIT 5`|Returns top 5 most expensive products|

---

## 3. Real-World Example

Suppose we have a **Products table**:

|product_id|name|price|category|stock|
|---|---|---|---|---|
|1|Laptop|999.99|Electronics|50|
|2|Mouse|25.50|Electronics|200|
|3|Chair|75.00|Furniture|100|
|4|Desk|150.00|Furniture|20|

### Step 1: Sort by price ascending

```SQL
SELECT name, price
FROM products
ORDER BY price ASC;

```

✅ Returns: Mouse, Chair, Desk, Laptop

### Step 2: Sort by price descending

```SQL
SELECT name, price
FROM products
ORDER BY price DESC;

```

✅ Returns: Laptop, Desk, Chair, Mouse

### Step 3: Sort by multiple columns

```SQL
SELECT name, category, price
FROM products
ORDER BY category ASC, price DESC;

```

✅ Returns:

1. Electronics → Laptop, Mouse (sorted by price descending)
2. Furniture → Desk, Chair (sorted by price descending)

### Step 4: Combine with WHERE and LIMIT

```SQL
SELECT name, price
FROM products
WHERE stock > 20
ORDER BY price DESC
LIMIT 3;

```

✅ Returns the **top 3 most expensive products in stock**: Laptop, Desk, Chair

---

## ✅ Key Takeaways

- `ORDER BY` **controls the sorting** of query results.
- Default is **ascending (**`**ASC**`**)**, descending requires `DESC`.
- Can sort by **multiple columns** for precise ordering.
- Often combined with **WHERE**, **LIMIT**, and **DISTINCT** for filtered and sorted results.