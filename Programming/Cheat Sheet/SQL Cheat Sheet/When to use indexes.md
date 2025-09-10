---
Created: 2025-09-09T20:18
tags:
  - Indexes
---
## 1. Full Explanation

### 🔹 Why Use Indexes?

- Indexes **speed up query performance** by allowing the database to **quickly locate rows** without scanning the entire table.
- They are especially useful for **large tables** or **frequently queried columns**.
- But **indexes also have costs**: slower `INSERT`, `UPDATE`, `DELETE`, and additional storage.
- Proper use of indexes **balances performance and resource usage**.

---

### 🔹 When to Use Indexes

1. **Frequently used columns in WHERE clauses**
    
    - Example: Searching for a specific customer by `customer_id`.
    
    ```SQL
    SELECT * FROM customers
    WHERE customer_id = 101;
    
    ```
    
2. **Columns used in JOIN conditions**
    
    - Example: Joining `orders` and `customers` on `customer_id`.
    
    ```SQL
    SELECT o.order_id, c.name
    FROM orders o
    JOIN customers c ON o.customer_id = c.customer_id;
    
    ```
    
3. **Columns used in ORDER BY or GROUP BY**
    
    - Speeds up **sorting** and **grouping** operations.
    
    ```SQL
    SELECT * FROM employees
    ORDER BY salary DESC;
    
    ```
    
4. **Columns used in aggregate functions for filtering**
    - Example: `MAX`, `MIN`, `COUNT` on indexed columns.
5. **Columns with high selectivity**
    - Columns with **many unique values** (e.g., `email`, `username`) are ideal.
    - Avoid indexing columns with **few unique values** (e.g., gender) unless used in combination.
6. **Primary keys and foreign keys**
    - Automatically indexed in most DBMS.
    - Essential for **referential integrity** and fast lookups.
7. **Composite indexes for multi-column searches**
    - Useful if queries frequently filter **on multiple columns** together.

---

### 🔹 When Not to Use Indexes

- On **small tables** (full table scan is already fast).
- On columns with **low selectivity** (few unique values).
- On columns that are **frequently updated**, unless necessary.
- Excessive indexes → **higher storage cost** and slower writes.

---

## 2. Summary Table (Quick Reference)

|Use Case|Should You Index?|Notes|
|---|---|---|
|Column in WHERE clause|✅ Yes|High selectivity preferred|
|Column in JOIN condition|✅ Yes|Speeds up joins|
|Column in ORDER BY / GROUP BY|✅ Yes|Speeds up sorting/grouping|
|Column frequently updated|❌ Be careful|Index maintenance slows updates|
|Column with few unique values|❌ Usually no|Low performance benefit|
|Primary / foreign keys|✅ Yes|Usually automatic|
|Multi-column queries|✅ Use composite|Cover queries efficiently|

---

## 3. Real-World Example

Suppose we have **Orders table** with 1 million rows:

|order_id|customer_id|order_date|total|
|---|---|---|---|

- Frequently queried by `customer_id` → **index on customer_id**
- Frequently sorted by `order_date` → **index on order_date**
- Frequently filtered by `customer_id` AND `order_date` → **composite index (customer_id, order_date)**

```SQL
CREATE INDEX idx_customer_id ON orders(customer_id);
CREATE INDEX idx_order_date ON orders(order_date);
CREATE INDEX idx_customer_date ON orders(customer_id, order_date);

```

✅ Queries run significantly faster without scanning all rows.

---

## ✅ Key Takeaways

- Use indexes to **speed up reads**, especially on **large tables**.
- Focus on **columns frequently used in WHERE, JOIN, ORDER BY, GROUP BY, or aggregates**.
- Avoid unnecessary indexes on **small, low-selectivity, or heavily updated columns**.
- Use **composite indexes** when multiple columns are frequently filtered together.
- Indexes **improve query speed** but **increase storage and slow writes**—balance is key.