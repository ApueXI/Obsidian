## SQL Roadmap

### 🔰 1. **Basics & Foundations**

- What is SQL? (Declarative, not procedural)
- SQL vs NoSQL
- Databases, Tables, Rows, Columns
- Data types (numeric, text, date/time, boolean)
- NULL values

---

### 🗂️ 2. **Data Definition Language (DDL)**

- `CREATE DATABASE`
- `CREATE TABLE` (columns, data types, constraints)
- `ALTER TABLE` (add, modify, drop column)
- `DROP TABLE`
- Constraints:
    - `PRIMARY KEY`
    - `FOREIGN KEY`
    - `UNIQUE`
    - `CHECK`
    - `NOT NULL`
    - `DEFAULT`

---

### 📥 3. **Data Manipulation Language (DML)**

- `INSERT INTO` (single & multiple rows)
- `UPDATE` (with `WHERE`)
- `DELETE` (with `WHERE`)

---

### 🔍 4. **Basic Queries (SELECT)**

- `SELECT column1, column2 FROM table;`
- `DISTINCT`
- `WHERE` (filters with comparison, `=`, `!=`, `<`, `>`, `<=`, `>=`)
- Logical operators (`AND`, `OR`, `NOT`)
- `BETWEEN`, `IN`, `LIKE`, `IS NULL`

---

### 📊 5. **Sorting & Limiting**

- `ORDER BY` (ASC, DESC)
- `LIMIT` / `OFFSET` (or `FETCH FIRST n ROWS`)

---

### 🧮 6. **Aggregations**

- Aggregate functions:
    - `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
- `GROUP BY`
- `HAVING` (filters after aggregation)

---

### 🔗 7. **Joins**

- `INNER JOIN`
- `LEFT JOIN` / `LEFT OUTER JOIN`
- `RIGHT JOIN` / `RIGHT OUTER JOIN`
- `FULL OUTER JOIN`
- `CROSS JOIN`
- Self joins

---

### 🗂️ 8. **Subqueries**

- Scalar subqueries (single value)
- Row subqueries
- Table subqueries
- `IN` with subqueries
- `EXISTS` vs `NOT EXISTS`

---

### 📝 9. **Set Operations**

- `UNION`
- `UNION ALL`
- `INTERSECT`
- `EXCEPT` / `MINUS` (depends on SQL dialect)

---

### 🔐 10. **Transactions & Concurrency**

- `BEGIN TRANSACTION` / `START TRANSACTION`
- `COMMIT`
- `ROLLBACK`
- Isolation levels (Read Uncommitted, Read Committed, Repeatable Read, Serializable — theory)
- Locks (conceptual understanding)

---

### 📚 11. **Views**

- Creating views (`CREATE VIEW`)
- Updating views (if updatable)
- Dropping views (`DROP VIEW`)

---

### 🧩 12. **Indexes (Concept)**

- `CREATE INDEX` (basic indexing)
- Clustered vs Non-clustered (theory)
- When to use indexes
- Dropping indexes

---

### 🧠 13. **Advanced Querying**

- `CASE WHEN` expressions
- `COALESCE` & `NULLIF`
- Window functions:
    - `OVER()`
    - Ranking: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`
    - Aggregates with `OVER()` (running totals, moving averages)

---

### 🗄️ 14. **Schema Management**

- Schemas vs Databases (concepts)
- `CREATE SCHEMA`
- Managing multiple schemas

---

### 🛡️ 15. **Security & Permissions**

- `CREATE USER` (if supported)
- `GRANT` privileges
- `REVOKE` privileges
- Roles (conceptual)

---

### 📊 16. **Normalization & Database Design**

- 1NF, 2NF, 3NF, BCNF
- Primary keys & surrogate keys
- Referential integrity
- Denormalization (trade-offs)

---

### 🌀 17. **Optional Built-in Extras (ANSI SQL Standard)**

- `CHECK` constraints with expressions
- Triggers (basic understanding, though closer to procedural SQL)
- `DEFAULT` expressions (`CURRENT_DATE`, `CURRENT_TIMESTAMP`)

---

## ✅ What You Can Do with Pure SQL:

- Design relational databases
- Query and filter data efficiently
- Combine multiple tables with joins
- Summarize & aggregate data
- Manage users & permissions
- Ensure data integrity with constraints
- Build reporting queries with grouping and window functions

  