---
Created: 2025-09-09T19:53
tags:
  - Aggregations
---
## 1. Full Explanation

### 🔹 What is `HAVING`?

- `HAVING` is used in **SELECT queries with GROUP BY**.
- It **filters groups** based on aggregate conditions.
- Unlike `WHERE`, which filters **individual rows**, `HAVING` filters **aggregated results**.

### 🔹 General Syntax

```SQL
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE row_condition
GROUP BY column1
HAVING aggregate_function(column2) group_condition
ORDER BY column1;

```

**Notes:**

- `HAVING` is applied **after grouping**.
- Can use **any aggregate function** in the condition (`COUNT`, `SUM`, `AVG`, etc.).
- Often combined with `WHERE` to filter rows **before aggregation**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Filter groups with HAVING|`HAVING COUNT(*) > 5`|Only include groups with more than 5 rows|
|Use with SUM|`HAVING SUM(amount) > 1000`|Groups with total amount > 1000|
|Use with AVG|`HAVING AVG(age) < 30`|Groups with average age < 30|
|Combine with WHERE|`WHERE status='active' HAVING SUM(amount)>500`|Filters rows first, then groups|
|Multiple aggregate conditions|`HAVING COUNT(*) > 5 AND SUM(amount) > 1000`|Multiple conditions on groups|

---

## 3. Real-World Example

Suppose we have an **Orders table**:

|order_id|customer|amount|status|
|---|---|---|---|
|1|Alice|100|completed|
|2|Bob|50|pending|
|3|Alice|200|completed|
|4|Charlie|150|completed|
|5|Bob|75|completed|
|6|Alice|50|pending|

### Step 1: Count orders per customer

```SQL
SELECT customer, COUNT(*) AS order_count
FROM orders
GROUP BY customer;

```

✅ Returns:

- Alice → 3
- Bob → 2
- Charlie → 1

### Step 2: Filter groups with HAVING

```SQL
SELECT customer, COUNT(*) AS order_count
FROM orders
GROUP BY customer
HAVING COUNT(*) > 2;

```

✅ Returns:

- Alice → 3

### Step 3: Filter groups using SUM

```SQL
SELECT customer, SUM(amount) AS total_amount
FROM orders
GROUP BY customer
HAVING SUM(amount) > 200;

```

✅ Returns:

- Alice → 350

### Step 4: Combine WHERE and HAVING

```SQL
SELECT customer, SUM(amount) AS total_completed
FROM orders
WHERE status = 'completed'
GROUP BY customer
HAVING SUM(amount) > 200;

```

✅ Returns:

- Alice → 300

---

## ✅ Key Takeaways

- `HAVING` filters **groups**, not individual rows.
- Works with **aggregate functions** like `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`.
- Often used **after GROUP BY**, and optionally combined with `WHERE`.
- Essential for **summary reports and analytics**.