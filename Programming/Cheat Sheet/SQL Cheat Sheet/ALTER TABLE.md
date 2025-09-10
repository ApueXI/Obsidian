---
Created: 2025-09-09T19:26
tags:
  - Data-Definition-Language-(DDL)
---
## 1. Full Explanation

### 🔹 What is `ALTER TABLE`?

- `ALTER TABLE` is a **Data Definition Language (DDL)** command.
- It is used to **modify the structure of an existing table** without dropping it.
- Common uses include:
    - Adding or removing columns
    - Changing column data types
    - Adding or dropping constraints
    - Renaming columns or tables

### 🔹 General Syntax

1. **Add a column**

```SQL
ALTER TABLE table_name
ADD column_name datatype [constraints];

```

1. **Drop a column**

```SQL
ALTER TABLE table_name
DROP COLUMN column_name;

```

1. **Modify a column** (change datatype or constraints)

```SQL
ALTER TABLE table_name
MODIFY column_name new_datatype [constraints];  -- MySQL
ALTER TABLE table_name
ALTER COLUMN column_name TYPE new_datatype;     -- PostgreSQL

```

1. **Add a constraint**

```SQL
ALTER TABLE table_name
ADD CONSTRAINT constraint_name PRIMARY KEY (column_name);

```

1. **Drop a constraint**

```SQL
ALTER TABLE table_name
DROP CONSTRAINT constraint_name;  -- PostgreSQL
ALTER TABLE table_name
DROP PRIMARY KEY;                -- MySQL

```

---

## 2. Summary Table (Quick Reference)

|**Operation**|**Syntax / Example**|**Notes**|
|---|---|---|
|Add column|`ALTER TABLE users ADD age INT;`|Adds new column `age`|
|Drop column|`ALTER TABLE users DROP COLUMN age;`|Removes column `age`|
|Change data type|`ALTER TABLE users MODIFY age BIGINT;` (MySQL)|Changes column type|
|Rename column|`ALTER TABLE users RENAME COLUMN age TO user_age;`|Renames a column|
|Add primary key|`ALTER TABLE users ADD PRIMARY KEY (id);`|Sets primary key|
|Add foreign key|`ALTER TABLE orders ADD FOREIGN KEY (user_id) REFERENCES users(id);`|Links tables|
|Drop primary key|`ALTER TABLE users DROP PRIMARY KEY;`|Removes PK|
|Rename table|`ALTER TABLE users RENAME TO customers;`|Renames table|

---

## 3. Real-World Example

Suppose we have a table `users`:

```SQL
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    name VARCHAR(100)
);

```

### Step 1: Add a new column

```SQL
ALTER TABLE users ADD email VARCHAR(100);

```

### Step 2: Modify a column data type

```SQL
ALTER TABLE users MODIFY name VARCHAR(150);  -- MySQL

```

### Step 3: Add a default value to a column

```SQL
ALTER TABLE users ALTER COLUMN email SET DEFAULT 'noemail@example.com';  -- PostgreSQL

```

### Step 4: Rename a column

```SQL
ALTER TABLE users RENAME COLUMN name TO full_name;

```

### Step 5: Add a new table constraint

```SQL
ALTER TABLE users ADD CONSTRAINT unique_email UNIQUE (email);

```

---

## ✅ Key Takeaways

- `ALTER TABLE` is **safe for evolving table structures** without losing existing data.
- Be careful when dropping or modifying columns—data may be lost.
- Useful for **adding new features** to an existing schema (like new columns or constraints).