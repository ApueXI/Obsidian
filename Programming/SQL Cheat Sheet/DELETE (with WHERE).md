---
Created: 2025-09-09T19:41
tags:
  - Data-Manipulation-Language-(DML)
---
## 1. Full Explanation

### 🔹 What is `DELETE`?

- `DELETE` is a **Data Manipulation Language (DML)** command.
- It **removes existing rows** from a table.
- Always use `WHERE` to **specify which rows to delete**; omitting `WHERE` deletes **all rows**.

### 🔹 General Syntax

```SQL
DELETE FROM table_name
WHERE condition;

```

**Notes:**

- `WHERE` filters which rows are deleted.
- Without `WHERE`, all rows in the table will be removed.
- Deleting a row that is referenced by a **foreign key** may fail unless `ON DELETE CASCADE` is set.

---

## 2. Summary Table (Quick Reference)

|**Operation**|**Syntax / Example**|**Notes**|
|---|---|---|
|Delete a single row|`DELETE FROM users WHERE user_id = 1;`|Deletes the row with user_id 1|
|Delete multiple rows|`DELETE FROM users WHERE status = 'inactive';`|Deletes all inactive users|
|Delete all rows (no WHERE)|`DELETE FROM users;`|Removes all rows, keeps table structure|
|Delete with foreign key|`DELETE FROM orders WHERE user_id = 2;`|Ensure FK rules allow deletion|
|Delete using subquery|`DELETE FROM users WHERE user_id IN (SELECT user_id FROM orders WHERE amount = 0);`|Conditional delete based on another table|

---

## 3. Real-World Example

Suppose we have a **Users table**:

|user_id|name|email|status|
|---|---|---|---|
|1|Alice|alice@email.com|active|
|2|Bob|bob@email.com|inactive|
|3|Charlie|charlie@email.com|active|

### Step 1: Delete a single row

```SQL
DELETE FROM users
WHERE user_id = 2;

```

✅ Bob’s row is deleted.

### Step 2: Delete multiple rows with a condition

```SQL
DELETE FROM users
WHERE status = 'inactive';

```

✅ All users with status `inactive` are removed.

### Step 3: Delete all rows (keep table)

```SQL
DELETE FROM users;

```

✅ Table is now empty, structure remains intact.

---

## ✅ Key Takeaways

- Always use `**WHERE**` to avoid deleting **all rows unintentionally**.
- Works with **foreign key constraints**, so deletion may fail if dependent rows exist.
- Use `TRUNCATE TABLE` if you want to quickly remove all rows and reset auto-increment counters.
- Part of **CRUD** operations: `INSERT`, `SELECT`, `UPDATE`, `DELETE`.