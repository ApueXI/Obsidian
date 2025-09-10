---
Created: 2025-09-09T19:22
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 Database

- A **database** is a structured collection of data stored electronically.
- Think of it as a **filing cabinet** where all your information lives.
- A single server can host **multiple databases**.
- Examples: `shop`, `school`, `banking_system`.

### 🔹 Table

- A **table** is like a **spreadsheet** inside a database.
- It organizes data into **rows and columns**.
- Each table usually represents an **entity** (e.g., `Users`, `Orders`, `Products`).

### 🔹 Row (Record / Tuple)

- A **row** represents a **single record** in a table.
- Example: one customer, one order, one product.
- Each row is **unique** and identified by a **primary key** (like an ID).

### 🔹 Column (Field / Attribute)

- A **column** defines the **type of data stored** (name, email, price).
- Each column has a **data type** (INT, VARCHAR, DATE, DECIMAL, etc.).
- Example: `id INT`, `name VARCHAR(100)`, `price DECIMAL(10,2)`.

---

## 2. Summary Table (Quick Reference)

|**Concept**|**Definition**|**Example**|
|---|---|---|
|**Database**|Collection of related tables|`shop`|
|**Table**|Stores structured data in rows/columns|`users`|
|**Row**|Single record (tuple)|`{ id: 1, name: 'Alice' }`|
|**Column**|Attribute/field (data type)|`name VARCHAR(100)`|

---

## 3. Real-World Example

Let’s say we have a database for an **online shop**:

### Step 1: Create a database

```SQL
CREATE DATABASE shop;

```

### Step 2: Create a table

```SQL
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

```

### Step 3: Insert rows (records)

```SQL
INSERT INTO users (user_id, name, email)
VALUES
(1, 'Alice', 'alice@email.com'),
(2, 'Bob', 'bob@email.com');

```

### Step 4: What it looks like

**Database:** `**shop**`

📂 Tables → `users`

**Table:** `**users**`

|user_id|name|email|
|---|---|---|
|1|Alice|alice@email.com|
|2|Bob|bob@email.com|

- **Database** = `shop`
- **Table** = `users`
- **Row** = `{1, Alice, alice@email.com}`
- **Column** = `name`, `email`