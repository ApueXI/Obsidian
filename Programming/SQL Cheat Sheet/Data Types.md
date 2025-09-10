---
Created: 2025-09-09T19:23
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

In SQL, every **column** must have a **data type**.

- It defines the **kind of values** that column can hold.
- Helps the database **optimize storage** and **ensure data integrity**.

Data types vary slightly across SQL dialects (MySQL, PostgreSQL, SQL Server, Oracle), but the core categories are common.

---

### 🔹 Categories of Data Types

1. **Numeric Types** – for numbers (integers, decimals, floats).
2. **String/Text Types** – for text data.
3. **Date/Time Types** – for dates and timestamps.
4. **Boolean** – true/false values.
5. **Binary / Large Object Types** – images, files, long text.

---

## 2. Summary Table (Quick Reference)

|**Category**|**Data Type**|**Description**|**Example**|
|---|---|---|---|
|Numeric|`INT` / `INTEGER`|Whole numbers|`25`|
||`BIGINT`|Large integers|`1234567890`|
||`DECIMAL(p,s)` / `NUMERIC`|Fixed-point, exact|`123.45`|
||`FLOAT` / `REAL`|Approximate decimal|`3.14159`|
|String/Text|`CHAR(n)`|Fixed-length string|`'ABC'`|
||`VARCHAR(n)`|Variable-length string|`'Hello'`|
||`TEXT`|Large text data|`'This is a long note...'`|
|Date/Time|`DATE`|Stores date|`2025-09-09`|
||`TIME`|Stores time|`14:30:00`|
||`DATETIME` / `TIMESTAMP`|Date + Time|`2025-09-09 14:30:00`|
|Boolean|`BOOLEAN` / `BOOL`|True/False|`TRUE`, `FALSE`|
|Binary/LOB|`BLOB`|Binary data (images, files)|`0xFFD8FFE0...`|
||`CLOB` / `TEXT`|Character large object|A book’s content|

---

## 3. Real-World Example

Imagine we’re building a **Products table** for an online shop:

```SQL
CREATE TABLE products (
    product_id INT PRIMARY KEY,          -- Integer ID
    name VARCHAR(100) NOT NULL,          -- Product name
    price DECIMAL(10,2) NOT NULL,        -- Exact price with 2 decimals
    stock INT DEFAULT 0,                 -- Quantity available
    is_active BOOLEAN DEFAULT TRUE,      -- Active or not
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- Creation date/time
);

```

### Insert sample rows:

```SQL
INSERT INTO products (product_id, name, price, stock)
VALUES
(1, 'Laptop', 999.99, 50),
(2, 'Mouse', 25.50, 200);

```

### Resulting table:

|product_id|name|price|stock|is_active|created_at|
|---|---|---|---|---|---|
|1|Laptop|999.99|50|TRUE|2025-09-09 19:05:00|
|2|Mouse|25.50|200|TRUE|2025-09-09 19:05:00|

---

## ✅ Key Takeaways

- Choose the **right data type** to save space and prevent invalid data.
- Use `DECIMAL` for money instead of `FLOAT` (to avoid rounding issues).
- Use `VARCHAR` instead of `TEXT` if the length is predictable.
- Always define constraints (`NOT NULL`, `DEFAULT`, `CHECK`) with data types for **data integrity**.