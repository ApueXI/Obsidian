---
Created: 2025-09-09T19:26
tags:
  - Data-Definition-Language-(DDL)
---
## 1. Full Explanation

### 🔹 What is `CREATE DATABASE`?

- `CREATE DATABASE` is a **Data Definition Language (DDL)** command.
- It creates a **new database** in the SQL server.
- A database can contain multiple **tables, views, stored procedures, and other objects**.

### 🔹 General Syntax

```SQL
CREATE DATABASE database_name;

```

- `database_name` must be **unique** on the server.
- Some SQL systems allow **options** (character set, collation, file location).

---

## 2. Summary Table (Quick Reference)

|**Command**|**Usage Example**|**Notes**|
|---|---|---|
|Basic create|`CREATE DATABASE shop;`|Creates database named `shop`|
|With charset (MySQL)|`CREATE DATABASE shop CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;`|Controls encoding/collation|
|Check existing DBs|`SHOW DATABASES;` (MySQL) / `\l` (Postgres)|Lists databases|
|Drop database|`DROP DATABASE shop;`|Deletes database (careful!)|
|Use database|`USE shop;` (MySQL/SQL Server) / `\c shop` (Postgres)|Switch context to a DB|

---

## 3. Real-World Example

Let’s say we want to create a database for an **online store**.

### Step 1: Create the database

```SQL
CREATE DATABASE shop;

```

### Step 2: Switch to it (MySQL / SQL Server)

```SQL
USE shop;

```

(PostgreSQL uses: `\c shop` in psql.)

### Step 3: Create a table inside it

```SQL
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    stock INT DEFAULT 0
);

```

### Step 4: Verify

```SQL
SHOW TABLES;   -- MySQL
\dt            -- PostgreSQL

```

---

## ✅ Key Takeaways

- `CREATE DATABASE` initializes a new database container.
- Always name databases clearly (e.g., `school_db`, `inventory`).
- Use **character set & collation** for language/encoding support.
- Use `DROP DATABASE` with caution—it deletes everything inside.