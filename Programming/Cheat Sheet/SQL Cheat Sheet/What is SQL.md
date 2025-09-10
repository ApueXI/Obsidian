---
Created: 2025-09-09T19:22
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 What is SQL?

- **SQL (Structured Query Language)** is a standard programming language used to interact with **relational databases**.
- It allows you to **create**, **read**, **update**, and **delete** data (often abbreviated as **CRUD**).
- SQL is used in most database systems (MySQL, PostgreSQL, SQLite, SQL Server, Oracle, etc.) with slight dialect differences.

### 🔹 Main Features

- **Declarative language** → you tell the database _what_ you want, not _how_ to do it.
- **Standardized** → governed by ANSI and ISO, though implementations vary.
- **Works with relational data** → tables with rows and columns.

### 🔹 Common Use Cases

- Querying data (find all customers in the US).
- Inserting new records (add a new order).
- Updating data (change a customer’s address).
- Deleting data (remove inactive users).
- Managing database schema (create/alter tables).
- Enforcing security (user permissions, roles).

---

## 2. Summary Table (Quick Reference)

|**Category**|**Command**|**Usage Example**|
|---|---|---|
|Create database|`CREATE DATABASE`|`CREATE DATABASE shop;`|
|Drop database|`DROP DATABASE`|`DROP DATABASE shop;`|
|Create table|`CREATE TABLE`|`CREATE TABLE users (id INT, name VARCHAR(100));`|
|Insert data|`INSERT INTO`|`INSERT INTO users (id, name) VALUES (1, 'Alice');`|
|Select data|`SELECT`|`SELECT * FROM users;`|
|Filter data|`WHERE`|`SELECT * FROM users WHERE id = 1;`|
|Update data|`UPDATE`|`UPDATE users SET name = 'Bob' WHERE id = 1;`|
|Delete data|`DELETE`|`DELETE FROM users WHERE id = 1;`|
|Sort results|`ORDER BY`|`SELECT * FROM users ORDER BY name;`|
|Aggregate|`COUNT, AVG, SUM`|`SELECT COUNT(*) FROM users;`|
|Join tables|`JOIN`|`SELECT u.name, o.amount FROM users u JOIN orders o ON u.id = o.user_id;`|
|Create index|`CREATE INDEX`|`CREATE INDEX idx_name ON users(name);`|
|Grant permission|`GRANT`|`GRANT SELECT ON users TO reader;`|

---

## 3. Real-World Example

Imagine you’re building an **e-commerce website**. You have two tables:

```SQL
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    amount DECIMAL(10,2),
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

```

### Example Queries:

- **Get all users who placed an order above $100**:

```SQL
SELECT u.name, o.amount
FROM users u
JOIN orders o ON u.user_id = o.user_id
WHERE o.amount > 100;

```

- **Insert a new user and order**:

```SQL
INSERT INTO users (user_id, name, email)
VALUES (1, 'Alice', 'alice@email.com');

INSERT INTO orders (order_id, user_id, amount)
VALUES (101, 1, 150.50);

```

- **Update user info**:

```SQL
UPDATE users
SET email = 'newalice@email.com'
WHERE user_id = 1;

```

- **Delete a user and their orders**:

```SQL
DELETE FROM orders WHERE user_id = 1;
DELETE FROM users WHERE user_id = 1;

```