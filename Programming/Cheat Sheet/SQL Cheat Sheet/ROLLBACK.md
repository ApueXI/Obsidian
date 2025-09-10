---
Created: 2025-09-09T20:11
tags:
  - Transactions-&-Concurrency
---
## 1. Full Explanation

### 🔹 What is `ROLLBACK`?

- `ROLLBACK` **undoes all changes** made during the current transaction.
- Used to **cancel a transaction** if an error occurs or conditions aren’t met.
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

-- Undo changes
ROLLBACK;

```

**Notes:**

- After a `ROLLBACK`, the database **returns to its state before the transaction started**.
- Can also use **SAVEPOINT** for partial rollbacks.
- Cannot rollback changes that were already **committed**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Rollback a transaction|`ROLLBACK;`|Undo all changes in current transaction|
|Must follow START/BEGIN|Transaction must be active|Otherwise error in some DBMS|
|Cannot rollback committed changes|Only uncommitted changes are undone|COMMIT makes changes permanent|
|Partial rollback|`ROLLBACK TO SAVEPOINT savepoint_name;`|Optional advanced feature|
|Typical use|Errors, validation failures, testing|Ensures database consistency|

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

### Step 2: Rollback changes

```SQL
ROLLBACK;

```

✅ After ROLLBACK:

|account_id|name|balance|
|---|---|---|
|1|Alice|500|
|2|Bob|300|

> Note: Both updates are undone, returning balances to their original values.

---

### Step 3: Partial rollback with SAVEPOINT

```SQL
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
SAVEPOINT before_bob_update;

UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

-- Rollback only Bob’s update
ROLLBACK TO SAVEPOINT before_bob_update;

COMMIT;

```

✅ Alice’s balance is updated, Bob’s update is **undone**, and the transaction is **partially committed**.

---

## ✅ Key Takeaways

- `ROLLBACK` **undoes all changes** in the current transaction.
- Must be used **before COMMIT**; once committed, changes cannot be undone.
- Essential for **error handling, validation, and testing** in transactional operations.
- Can use **SAVEPOINT** for **partial rollbacks** within a transaction.
- Complements **COMMIT** to maintain database integrity and ACID compliance.