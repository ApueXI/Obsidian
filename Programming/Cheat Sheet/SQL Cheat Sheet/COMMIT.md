---
Created: 2025-09-09T20:11
tags:
  - Transactions-&-Concurrency
---
## 1. Full Explanation

### 🔹 What is `COMMIT`?

- `COMMIT` is used to **permanently save all changes** made during a transaction to the database.
- After a `COMMIT`, **all operations in the transaction cannot be rolled back**.
- Works together with `BEGIN TRANSACTION` / `START TRANSACTION`.

### 🔹 General Syntax

```SQL
-- Start a transaction
START TRANSACTION;  -- MySQL, PostgreSQL
-- or
BEGIN TRANSACTION;  -- SQL Server, MS Access

-- SQL statements
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

-- Save changes permanently
COMMIT;

```

**Notes:**

- If **COMMIT is not executed**, changes may remain **uncommitted** depending on the DBMS.
- Auto-commit mode (default in many DBMS like MySQL) **commits each statement automatically**, but explicit transactions give more control.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Commit a transaction|`COMMIT;`|Saves all changes permanently|
|Must be after START/BEGIN|Transaction must be active|Otherwise error in some DBMS|
|Cannot be undone|Changes are permanent|Use ROLLBACK before commit to undo|
|Auto-commit mode|Varies by DBMS|Explicit COMMIT optional if auto-commit is enabled|
|Typical use|Financial transfers, batch updates, multi-step changes|Ensures consistency|

---

## 3. Real-World Example

Suppose we have **Accounts table**:

|account_id|name|balance|
|---|---|---|
|1|Alice|500|
|2|Bob|300|

### Step 1: Start transaction and perform updates

```SQL
START TRANSACTION;

UPDATE accounts
SET balance = balance - 100
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE account_id = 2;

```

### Step 2: Commit changes

```SQL
COMMIT;

```

✅ After COMMIT:

|account_id|name|balance|
|---|---|---|
|1|Alice|400|
|2|Bob|400|

> Note: After COMMIT, these changes are permanent and cannot be rolled back.

---

### Step 3: Example of forgetting COMMIT

```SQL
START TRANSACTION;

UPDATE accounts SET balance = balance - 50 WHERE account_id = 1;
-- COMMIT not executed

-- Changes might not be saved depending on DBMS

```

> Without COMMIT, the deduction may not persist unless the DBMS is in auto-commit mode.

---

## ✅ Key Takeaways

- `COMMIT` **permanently saves all changes** in a transaction.
- Must follow **START TRANSACTION / BEGIN TRANSACTION**.
- Cannot undo after commit; use **ROLLBACK** before commit if needed.
- Critical for **multi-step operations** to ensure database consistency.
- Auto-commit mode may make explicit COMMIT unnecessary, but explicit transactions are safer for **complex operations**.