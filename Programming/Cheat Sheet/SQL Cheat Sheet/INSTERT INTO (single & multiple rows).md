---
Created: 2025-09-09T19:39
tags:
  - Data-Manipulation-Language-(DML)
---
## 1. Full Explanation

### 🔹 What is `INSERT INTO`?

- `INSERT INTO` is a **Data Manipulation Language (DML)** command.
- It adds **new rows (records)** into a table.
- Can insert **one row at a time** or **multiple rows at once**.
- Works with tables that have constraints (`PRIMARY KEY`, `NOT NULL`, `DEFAULT`, etc.), respecting all rules.

---

### 🔹 General Syntax

**1. Single Row**

```SQL
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);

```

**2. Multiple Rows**

```SQL
INSERT INTO table_name (column1, column2, ...)
VALUES
    (value1a, value2a, ...),
    (value1b, value2b, ...),
    ...;

```

**Notes:**

- Columns listed must match the values in **number and order**.
- Columns with `DEFAULT` values or `AUTO_INCREMENT` can be skipped.

---

## 2. Summary Table (Quick Reference)

|**Operation**|**Syntax / Example**|**Notes**|
|---|---|---|
|Insert single row|`INSERT INTO users (id, name) VALUES (1, 'Alice');`|Basic insertion|
|Insert multiple rows|`INSERT INTO users (id, name) VALUES (2, 'Bob'), (3, 'Charlie');`|Efficient batch insert|
|Insert with default|`INSERT INTO users (id, name) VALUES (4, DEFAULT);`|Uses column default value|
|Skip AUTO_INCREMENT|`INSERT INTO users (name) VALUES ('Eve');`|ID auto-assigned|
|Insert all columns|`INSERT INTO users VALUES (5, 'Frank', 'frank@email.com');`|Must match table column order|

---

## 3. Real-World Example

Suppose we have a **Users table**:

```SQL
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    status VARCHAR(10) DEFAULT 'active'
);

```

### Step 1: Insert a single row

```SQL
INSERT INTO users (name, email)
VALUES ('Alice', 'alice@email.com');

```

### Step 2: Insert multiple rows

```SQL
INSERT INTO users (name, email)
VALUES
    ('Bob', 'bob@email.com'),
    ('Charlie', 'charlie@email.com'),
    ('Eve', 'eve@email.com');

```

### Step 3: Insert with default values

```SQL
INSERT INTO users (name)
VALUES ('Frank');  -- status will default to 'active'

```

### Step 4: Resulting table

|user_id|name|email|status|
|---|---|---|---|
|1|Alice|alice@email.com|active|
|2|Bob|bob@email.com|active|
|3|Charlie|charlie@email.com|active|
|4|Eve|eve@email.com|active|
|5|Frank|NULL|active|

---

## ✅ Key Takeaways

- `INSERT INTO` adds **new rows** to a table.
- Supports **single row** and **multiple row insertion**.
- Works seamlessly with **defaults** and **AUTO_INCREMENT** columns.
- Always respect **constraints** (`PRIMARY KEY`, `UNIQUE`, `NOT NULL`, etc.).