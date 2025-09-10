---
Created: 2025-09-09T19:54
tags:
  - Joins
---
## 1. Full Explanation

### 🔹 What is `LEFT JOIN`?

- `LEFT JOIN` (aka **LEFT OUTER JOIN**) returns **all rows from the left table**, and the **matching rows from the right table**.
- If there is **no match in the right table**, the result will show `NULL` for the right table’s columns.
- Useful for **keeping all records from the main table**, even if no related data exists in the joined table.

### 🔹 General Syntax

```SQL
SELECT table1.column1, table1.column2, table2.column1, table2.column2
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;

```

**Notes:**

- “LEFT JOIN” and “LEFT OUTER JOIN” are **interchangeable**.
- Returns all rows from the **left table**, filling `NULL` for missing matches in the right table.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic LEFT JOIN|`FROM customers LEFT JOIN orders ON customers.customer_id = orders.customer_id`|Returns all customers, even without orders|
|Select specific columns|`SELECT customers.name, orders.amount`|Choose which columns to display|
|Alias for tables|`FROM customers c LEFT JOIN orders o ON c.customer_id = o.customer_id`|Shorter references|
|Combine with WHERE|`WHERE orders.amount > 100`|Filter rows after join|
|LEFT OUTER JOIN|Same as LEFT JOIN|Optional keyword “OUTER”|

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
|103|1|200|

### Step 1: Basic LEFT JOIN

```SQL
SELECT customers.name, orders.amount
FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;

```

✅ Returns:

|name|amount|
|---|---|
|Alice|100|
|Alice|200|
|Bob|50|
|Charlie|NULL|

> Note: Charlie appears even though there is no order, and amount is NULL.

### Step 2: Using aliases

```SQL
SELECT c.name, o.amount
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;

```

✅ Same result with shorter references.

### Step 3: Combine with WHERE

```SQL
SELECT c.name, o.amount
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.amount > 50;

```

✅ Returns:

|name|amount|
|---|---|
|Alice|100|
|Alice|200|

> Note: Charlie is excluded because NULL > 50 is false.

---

## ✅ Key Takeaways

- `LEFT JOIN` keeps **all rows from the left table**, filling `NULL` for unmatched right table rows.
- Use `LEFT OUTER JOIN` if you want **explicit standard syntax** (same behavior).
- Often combined with **WHERE** or **aggregate functions** for reports.
- Essential for **finding missing relationships or optional data**.