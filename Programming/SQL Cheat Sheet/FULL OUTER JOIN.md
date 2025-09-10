---
Created: 2025-09-09T19:55
tags:
  - Joins
---
## 1. Full Explanation

### 🔹 What is `FULL OUTER JOIN`?

- `FULL OUTER JOIN` returns **all rows from both tables**.
- If there is a **match**, the rows are combined.
- If there is **no match**, the result will show `NULL` for the missing side.
- Useful for **finding all data**, including unmatched rows from both tables.

### 🔹 General Syntax

```SQL
SELECT table1.column1, table1.column2, table2.column1, table2.column2
FROM table1
FULL OUTER JOIN table2
ON table1.common_column = table2.common_column;

```

**Notes:**

- Some databases (e.g., MySQL) **don’t support FULL OUTER JOIN** natively; you can simulate it using **UNION of LEFT JOIN and RIGHT JOIN**.
- Combines the behavior of **LEFT JOIN** and **RIGHT JOIN**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic FULL OUTER JOIN|`FROM customers FULL OUTER JOIN orders ON customers.customer_id = orders.customer_id`|Returns all rows from both tables|
|Select specific columns|`SELECT customers.name, orders.amount`|Choose which columns to display|
|Alias for tables|`FROM customers c FULL OUTER JOIN orders o ON c.customer_id = o.customer_id`|Shorter references|
|Combine with WHERE|`WHERE amount > 50`|Filter rows after join|
|Alternative in MySQL|`LEFT JOIN ... UNION RIGHT JOIN ...`|Simulates FULL OUTER JOIN|

---

## 3. Real-World Example

Suppose we have **two tables**:

**Customers table**

|customer_id|name|email|
|---|---|---|
|1|Alice|alice@email.com|
|2|Bob|bob@email.com|
|3|Charlie|charlie@email.com|

**Orders table**

|order_id|customer_id|amount|
|---|---|---|
|101|1|100|
|102|2|50|
|103|4|200|

### Step 1: Basic FULL OUTER JOIN

```SQL
SELECT customers.name, orders.amount
FROM customers
FULL OUTER JOIN orders
ON customers.customer_id = orders.customer_id;

```

✅ Returns:

|name|amount|
|---|---|
|Alice|100|
|Bob|50|
|Charlie|NULL|
|NULL|200|

> Note: Charlie has no order → NULL in amount.
> 
> Order 103 has customer_id 4 → `NULL` in name.

### Step 2: Using aliases

```SQL
SELECT c.name, o.amount
FROM customers c
FULL OUTER JOIN orders o
ON c.customer_id = o.customer_id;

```

✅ Same result with shorter references.

### Step 3: Combine with WHERE

```SQL
SELECT c.name, o.amount
FROM customers c
FULL OUTER JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.amount > 50;

```

✅ Returns:

|name|amount|
|---|---|
|Alice|100|
|NULL|200|

> Note: Charlie is excluded because NULL > 50 is false.

---

## ✅ Key Takeaways

- `FULL OUTER JOIN` keeps **all rows from both tables**, filling `NULL` for unmatched rows.
- Combines the effect of **LEFT JOIN** and **RIGHT JOIN**.
- Useful for **complete data analysis**, including missing relationships.
- May require **UNION of LEFT and RIGHT JOIN** in databases like MySQL.