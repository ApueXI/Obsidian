---
Created: 2025-09-09T19:53
tags:
  - Aggregations
---
## 1. Full Explanation

### 🔹 What is `GROUP BY`?

- `GROUP BY` **groups rows** that have the same values in specified columns.
- Often used with **aggregate functions** (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`) to summarize data **per group**.
- You can filter groups with `HAVING` (like `WHERE` for individual rows).

### 🔹 General Syntax

```SQL
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1
HAVING aggregate_function(column2) condition
ORDER BY column1;

```

**Notes:**

- Columns in `SELECT` that are **not aggregated** must appear in `GROUP BY`.
- `HAVING` filters **groups**, while `WHERE` filters **rows**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Group rows by column|`GROUP BY category`|Groups rows by category|
|Aggregate per group|`SELECT category, SUM(price) FROM products GROUP BY category;`|Sum prices per category|
|Filter groups with HAVING|`HAVING SUM(price) > 100`|Filters groups based on aggregate|
|Combine with ORDER BY|`ORDER BY SUM(price) DESC`|Sort groups by aggregate|
|Multiple columns grouping|`GROUP BY department, role`|Group by multiple dimensions|

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

### Step 1: Count orders per customer

```SQL
SELECT customer, COUNT(*) AS order_count
FROM orders
GROUP BY customer;

```

✅ Returns:

- Alice → 2
- Bob → 2
- Charlie → 1

### Step 2: Sum of completed orders per customer

```SQL
SELECT customer, SUM(amount) AS total_amount
FROM orders
WHERE status = 'completed'
GROUP BY customer;

```

✅ Returns:

- Alice → 100 + 200 = 300
- Bob → 75
- Charlie → 150

### Step 3: Filter groups with HAVING

```SQL
SELECT customer, SUM(amount) AS total_amount
FROM orders
WHERE status = 'completed'
GROUP BY customer
HAVING SUM(amount) > 200;

```

✅ Returns: Alice → 300

### Step 4: Multiple columns grouping

```SQL
SELECT customer, status, COUNT(*) AS order_count
FROM orders
GROUP BY customer, status;

```

✅ Returns:

- Alice / completed → 2
- Bob / pending → 1
- Bob / completed → 1
- Charlie / completed → 1

---

## ✅ Key Takeaways

- `GROUP BY` **groups rows** for aggregation.
- Aggregate functions summarize data **per group**.
- Use `HAVING` to filter **groups**, unlike `WHERE` which filters **rows**.
- Can group by **multiple columns** for detailed summaries.