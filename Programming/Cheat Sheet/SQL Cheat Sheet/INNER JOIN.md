---
Created: 2025-09-09T19:54
tags:
  - Joins
---
## 1. Full Explanation

### 🔹 What is `INNER JOIN`?

- `INNER JOIN` combines rows from **two tables** based on a **matching condition**.
- Only returns rows where the **join condition is true** in **both tables**.
- Commonly used with **primary key – foreign key relationships**.

### 🔹 General Syntax

```SQL
SELECT table1.column1, table1.column2, table2.column1, table2.column2
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;

```

**Notes:**

- Only rows with **matching values in both tables** are included.
- Can join **multiple tables** using multiple INNER JOINs.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic INNER JOIN|`FROM orders INNER JOIN customers ON orders.customer_id = customers.customer_id`|Returns rows with matching customer_id|
|Select specific columns|`SELECT orders.id, customers.name`|Choose which columns to show|
|Multiple joins|`INNER JOIN table2 ON ... INNER JOIN table3 ON ...`|Join more than two tables|
|With WHERE condition|`WHERE orders.amount > 100`|Filter after join|
|Alias for tables|`FROM orders o INNER JOIN customers c ON o.customer_id = c.customer_id`|Shorter references|

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
|104|4|75|

### Step 1: Basic INNER JOIN

```SQL
SELECT orders.order_id, customers.name, orders.amount
FROM orders
INNER JOIN customers
ON orders.customer_id = customers.customer_id;

```

✅ Returns:

|order_id|name|amount|
|---|---|---|
|101|Alice|100|
|102|Bob|50|
|103|Alice|200|

> Note: Order 104 is excluded because customer_id 4 does not exist in Customers.

### Step 2: Using aliases

```SQL
SELECT o.order_id, c.name, o.amount
FROM orders o
INNER JOIN customers c
ON o.customer_id = c.customer_id;

```

✅ Same result, but easier to write with aliases.

### Step 3: Combine with WHERE

```SQL
SELECT o.order_id, c.name, o.amount
FROM orders o
INNER JOIN customers c
ON o.customer_id = c.customer_id
WHERE o.amount > 100;

```

✅ Returns:

|order_id|name|amount|
|---|---|---|
|103|Alice|200|

---

## ✅ Key Takeaways

- `INNER JOIN` returns rows **only when there is a match in both tables**.
- Can use **table aliases** to simplify queries.
- Often combined with **WHERE** to filter results.
- Excludes unmatched rows automatically (unlike LEFT JOIN).