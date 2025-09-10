---
Created: 2025-09-09T19:41
tags:
  - Data-Manipulation-Language-(DML)
---
## 1. Full Explanation

### 🔹 What is `UPDATE`?

- `UPDATE` is a **Data Manipulation Language (DML)** command.
- It **modifies existing rows** in a table.
- Always use `WHERE` to **specify which rows to update**; otherwise, all rows will be changed.

### 🔹 General Syntax

```SQL
UPDATE table_name
SET column1 = value1,
    column2 = value2,
    ...
WHERE condition;

```

**Notes:**

- `SET` defines the new values for columns.
- `WHERE` filters rows to update; **omit at your own risk**.
- You can update **one column** or **multiple columns** at once.

---

## 2. Summary Table (Quick Reference)

|**Operation**|**Syntax / Example**|**Notes**|
|---|---|---|
|Update single column|`UPDATE users SET name = 'Alice Smith' WHERE user_id = 1;`|Updates `name` for user_id 1|
|Update multiple columns|`UPDATE users SET name = 'Bob', status = 'inactive' WHERE user_id = 2;`|Updates multiple fields|
|Update all rows (no WHERE)|`UPDATE users SET status = 'inactive';`|All rows affected! Be careful|
|Conditional update|`UPDATE users SET status = 'inactive' WHERE last_login < '2025-01-01';`|Only updates old users|
|Use expressions|`UPDATE products SET price = price * 1.1 WHERE category = 'Electronics';`|Update using calculations|

---

## 3. Real-World Example

Suppose we have a **Users table**:

|user_id|name|email|status|
|---|---|---|---|
|1|Alice|alice@email.com|active|
|2|Bob|bob@email.com|active|
|3|Charlie|charlie@email.com|active|

### Step 1: Update a single row

```SQL
UPDATE users
SET status = 'inactive'
WHERE user_id = 2;

```

✅ Bob’s status is now `inactive`.

### Step 2: Update multiple columns

```SQL
UPDATE users
SET name = 'Alice Smith', email = 'alice.smith@email.com'
WHERE user_id = 1;

```

✅ Alice’s name and email are updated.

### Step 3: Update multiple rows with condition

```SQL
UPDATE users
SET status = 'inactive'
WHERE status = 'active';

```

✅ All users with status `active` are now `inactive`.

---

## ✅ Key Takeaways

- Always use `**WHERE**` to avoid unintentional mass updates.
- `UPDATE` can modify **one or multiple columns** at the same time.
- Can use **expressions or calculations** to update numeric fields.
- Works with **constraints** (`NOT NULL`, `CHECK`, etc.), so invalid updates may fail.