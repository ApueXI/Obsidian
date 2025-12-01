---
Created: 2025-09-09T19:52
tags:
  - Aggregations
---
### 🔹 What are Aggregate Functions?

- Aggregate functions **perform calculations on multiple rows** and return a **single value**.
- Commonly used with `GROUP BY` for summarizing data.

### 🔹 Common Aggregate Functions

|Function|Description|Example|
|---|---|---|
|`COUNT()`|Counts rows|`SELECT COUNT(*) FROM users;`|
|`SUM()`|Sum of values|`SELECT SUM(price) FROM orders;`|
|`AVG()`|Average of values|`SELECT AVG(age) FROM users;`|
|`MIN()`|Minimum value|`SELECT MIN(price) FROM products;`|
|`MAX()`|Maximum value|`SELECT MAX(age) FROM users;`|

**Notes:**

- Often used with `GROUP BY` to calculate per category or group.
- Can be combined with `WHERE` for filtered calculations.

---

## 2. Summary Table (Quick Reference)

| Function | Syntax / Example                                                  | Notes               |
| -------- | ----------------------------------------------------------------- | ------------------- |
| COUNT    | `SELECT COUNT(*) FROM users;`                                     | Counts all rows     |
| SUM      | `SELECT SUM(salary) FROM employees;`                              | Total sum of column |
| AVG      | `SELECT AVG(age) FROM users;`                                     | Average value       |
| MIN      | `SELECT MIN(price) FROM products;`                                | Smallest value      |
| MAX      | `SELECT MAX(price) FROM products;`                                | Largest value       |
| GROUP BY | `SELECT department, COUNT(*) FROM employees GROUP BY department;` | Aggregate per group |
| ROUND    | SELECT ROUND(AVG(age),n) FROM users;`                             | n = number          |

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

### Step 1: Count total orders

```SQL
SELECT COUNT(*) AS total_orders
FROM orders;

```

✅ Returns: 5

### Step 2: Sum of all completed orders

```SQL
SELECT SUM(amount) AS total_completed
FROM orders
WHERE status = 'completed';

```

✅ Returns: 100 + 200 + 150 + 75 = 525

### Step 3: Average order amount

```SQL
SELECT ROUND(AVG(amount),2) AS avg_order
FROM orders;

```

✅ Returns: (100 + 50 + 200 + 150 + 75) / 5 = 115

### Step 4: Min and Max amount

```SQL
SELECT MIN(amount) AS min_amount, MAX(amount) AS max_amount
FROM orders;

```

✅ Returns: Min = 50, Max = 200

### Step 5: Count orders per customer (GROUP BY)

```SQL
SELECT customer, COUNT(*) AS order_count
FROM orders
GROUP BY customer;

```

✅ Returns:

- Alice → 2
- Bob → 2
- Charlie → 1

---

## ✅ Key Takeaways

- Aggregate functions **summarize data** across rows.
- `GROUP BY` is used to calculate aggregates **per category or group**.
- Can be filtered using `WHERE` before aggregation.
- Common functions: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`.