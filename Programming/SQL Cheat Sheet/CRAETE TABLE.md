---
Created: 2025-09-09T19:26
tags:
  - Data-Definition-Language-(DDL)
---
## 1. Full Explanation

### 🔹 What is `CREATE TABLE`?

- `CREATE TABLE` is a **Data Definition Language (DDL)** command.
- It creates a **new table** inside a database to store structured data.
- Tables consist of **columns** (attributes/fields) and **rows** (records).

### 🔹 General Syntax

```SQL
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    ...
);

```

- `table_name`: Name of the table (unique within the database).
- `datatype`: Defines the type of data (`INT`, `VARCHAR`, `DECIMAL`, `DATE`, etc.).
- `constraints` (optional): Rules for the column (e.g., `PRIMARY KEY`, `NOT NULL`, `UNIQUE`).

---

## 2. Summary Table (Quick Reference)

|**Concept**|**Syntax / Example**|**Notes**|
|---|---|---|
|Create table|`CREATE TABLE users (id INT, name VARCHAR(100));`|Basic table with 2 columns|
|Primary key|`id INT PRIMARY KEY`|Uniquely identifies each row|
|Auto-increment|`id INT AUTO_INCREMENT` (MySQL)|Automatically increases ID|
|Not null|`name VARCHAR(50) NOT NULL`|Column cannot be empty|
|Unique|`email VARCHAR(100) UNIQUE`|Prevents duplicate values|
|Foreign key|`FOREIGN KEY (user_id) REFERENCES users(id)`|Links tables together|
|Default value|`status VARCHAR(10) DEFAULT 'active'`|Sets default if value not provided|
|Check constraint|`price DECIMAL(10,2) CHECK (price > 0)`|Validates column values|

---

## 3. Real-World Example

Imagine a **Products table** for an online shop:

```SQL
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2) NOT NULL CHECK (price > 0),
    stock INT DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

```

### Insert sample rows:

```SQL
INSERT INTO products (name, price, stock)
VALUES ('Laptop', 999.99, 50),
       ('Mouse', 25.50, 200);

```

### Resulting table:

|product_id|name|price|stock|created_at|
|---|---|---|---|---|
|1|Laptop|999.99|50|2025-09-09 19:20:00|
|2|Mouse|25.50|200|2025-09-09 19:20:00|

---

## ✅ Key Takeaways

- `CREATE TABLE` defines the **structure of your data**.
- Always define **primary keys** and **constraints** for data integrity.
- Use **appropriate data types** for each column to save space and prevent errors.
- Foreign keys allow you to **link tables** (relational database principle).