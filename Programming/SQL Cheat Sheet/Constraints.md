---
Created: 2025-09-09T19:26
tags:
  - Data-Definition-Language-(DDL)
---
## 1. Full Explanation

### 🔹 What are Constraints?

- Constraints are **rules applied to table columns** to enforce **data integrity**.
- They ensure that the data in the table is **accurate, consistent, and valid**.
- Common types: `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`, `NOT NULL`, `DEFAULT`.

---

## 2. Summary Table (Quick Reference)

|**Constraint**|**Description**|**Syntax / Example**|**Notes**|
|---|---|---|---|
|`PRIMARY KEY`|Uniquely identifies each row|`id INT PRIMARY KEY`|Only one per table, implicitly `NOT NULL`|
|`FOREIGN KEY`|Links a column to another table’s primary key|`user_id INT, FOREIGN KEY (user_id) REFERENCES users(id)`|Enforces referential integrity|
|`UNIQUE`|Ensures all values in a column are distinct|`email VARCHAR(100) UNIQUE`|Can have multiple per table|
|`CHECK`|Enforces a condition on values|`price DECIMAL CHECK (price > 0)`|Validates values|
|`NOT NULL`|Column must always have a value|`name VARCHAR(100) NOT NULL`|Cannot be left empty|
|`DEFAULT`|Provides a default value if none is specified|`status VARCHAR(10) DEFAULT 'active'`|Automatically applied during insert|

---

## 3. Real-World Example

Imagine a **Users table**:

```SQL
CREATE TABLE users (
    user_id INT PRIMARY KEY,                   -- Unique ID
    name VARCHAR(100) NOT NULL,                -- Cannot be null
    email VARCHAR(100) UNIQUE,                 -- Unique emails
    age INT CHECK (age >= 0),                  -- Age must be non-negative
    status VARCHAR(10) DEFAULT 'active',      -- Default value if not provided
    group_id INT,
    FOREIGN KEY (group_id) REFERENCES groups(group_id) -- Link to another table
);

```

### Step 1: Insert sample rows

```SQL
INSERT INTO users (user_id, name, email, age)
VALUES (1, 'Alice', 'alice@email.com', 25),
       (2, 'Bob', 'bob@email.com', 30);

```

### Step 2: Attempt violating constraints

```SQL
INSERT INTO users (user_id, name, email, age)
VALUES (2, 'Charlie', 'bob@email.com', -5);

```

✅ Results in **errors** because:

- `user_id` duplicates → violates `PRIMARY KEY`
- `email` duplicates → violates `UNIQUE`
- `age = -5` → violates `CHECK (age >= 0)`

---

## ✅ Key Takeaways

- Constraints **protect your data** and enforce rules automatically.
- Always define **PRIMARY KEY** for uniqueness.
- Use **FOREIGN KEY** to maintain relationships between tables.
- `NOT NULL`, `UNIQUE`, `CHECK`, and `DEFAULT` help ensure **data quality**.
- Violating constraints will **prevent invalid data from being inserted or updated**.