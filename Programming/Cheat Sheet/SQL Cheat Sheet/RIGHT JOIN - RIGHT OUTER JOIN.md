---
Created: 2025-09-09T19:55
tags:
  - Joins
---
## 1. Full Explanation

### 🔹 What is `RIGHT JOIN`?

- `RIGHT JOIN` (aka **RIGHT OUTER JOIN**) returns **all rows from the right table**, and the **matching rows from the left table**.
- If there is **no match in the left table**, the result will show `NULL` for the left table’s columns.
- Useful for **keeping all records from the secondary table**, even if no related data exists in the main table.

### 🔹 General Syntax

```SQL
SELECT table1.column1, table1.column2, table2.column1, table2.column2
FROM table1
RIGHT JOIN table2
ON table1.common_column = table2.common_column;

```

**Notes:**

- “RIGHT JOIN” and “RIGHT OUTER JOIN” are **interchangeable**.
- Returns all rows from the **right table**, filling `NULL` for missing matches in the left table.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic RIGHT JOIN|`FROM orders RIGHT JOIN customers ON orders.customer_id = customers.customer_id`|Returns all customers, even without orders|
|Select specific columns|`SELECT customers.name, orders.amount`|Choose which columns to display|
|Alias for tables|`FROM orders o RIGHT JOIN customers c ON o.customer_id = c.customer_id`|Shorter references|
|Combine with WHERE|`WHERE orders.amount > 100`|Filter rows after join|
|RIGHT OUTER JOIN|Same as RIGHT JOIN|Optional keyword “OUTER”|

---

## 3. Real-World Example

Suppose we have **two tables**:

**Orders table**

|order_id|customer_id|amount|
|---|---|---|
|101|1|100|
|102|2|50|
|103|1|200|

**Customers table**

|customer_id|name|email|
|---|---|---|
|1|Alice|alice@email.com|
|2|Bob|bob@email.com|
|3|Charlie|charlie@email.com|

### Step 1: Basic RIGHT JOIN

```SQL
SELECT orders.order_id, customers.name, orders.amount
FROM orders
RIGHT JOIN customers
ON orders.customer_id = customers.customer_id;

```

✅ Returns:

|order_id|name|amount|
|---|---|---|
|101|Alice|100|
|103|Alice|200|
|102|Bob|50|
|NULL|Charlie|NULL|

> Note: Charlie appears even though there is no order, and order_id and amount are NULL.

### Step 2: Using aliases

```SQL
SELECT o.order_id, c.name, o.amount
FROM orders o
RIGHT JOIN customers c
ON o.customer_id = c.customer_id;

```

✅ Same result with shorter references.

### Step 3: Combine with WHERE

```SQL
SELECT o.order_id, c.name, o.amount
FROM orders o
RIGHT JOIN customers c
ON o.customer_id = c.customer_id
WHERE o.amount > 50;

```

✅ Returns:

|order_id|name|amount|
|---|---|---|
|101|Alice|100|
|103|Alice|200|

> Note: Charlie is excluded because NULL > 50 is false.

---

## ✅ Key Takeaways

- `RIGHT JOIN` keeps **all rows from the right table**, filling `NULL` for unmatched left table rows.
- Use `RIGHT OUTER JOIN` if you want **explicit standard syntax** (same behavior).
- Often combined with **WHERE** or **aggregate functions** for reporting.
- Useful for **finding missing relationships or optional data** from the secondary table.