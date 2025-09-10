---
Created: 2025-09-09T20:11
tags:
  - Transactions-&-Concurrency
---
## 1. Full Explanation

### 🔹 What is a Transaction?

- A **transaction** is a **sequence of one or more SQL statements** executed as a single logical unit.
- Ensures **ACID properties**:
    - **Atomicity** – All statements succeed, or none do.
    - **Consistency** – Database remains consistent before and after the transaction.
    - **Isolation** – Transactions don’t interfere with each other.
    - **Durability** – Changes are permanent once committed.

### 🔹 `BEGIN TRANSACTION` / `START TRANSACTION`

- Used to **start a transaction**.
- After starting, you can perform multiple operations, then either **commit** or **rollback**.

**General Syntax:**

```SQL
-- Start a transaction
BEGIN TRANSACTION;  -- SQL Server, MS Access
-- or
START TRANSACTION;  -- MySQL, PostgreSQL, MariaDB

-- SQL statements
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

-- Commit changes
COMMIT;

-- OR rollback in case of error
ROLLBACK;

```

**Notes:**

- `COMMIT` makes all changes **permanent**.
- `ROLLBACK` undoes all changes **since the transaction started**.
- Transactions are **optional**, but recommended for **critical operations like money transfers**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Start transaction|`BEGIN TRANSACTION` / `START TRANSACTION`|Begin a logical unit of work|
|Commit transaction|`COMMIT;`|Make all changes permanent|
|Rollback transaction|`ROLLBACK;`|Undo changes since transaction started|
|Nested transactions|Varies by DBMS|Some DBMS support savepoints|
|Typical use|Money transfer, batch updates, multi-step changes|Ensures ACID properties|

---

## 3. Real-World Example

### Step 1: Money Transfer Transaction

Suppose we have **Accounts table**:

|account_id|name|balance|
|---|---|---|
|1|Alice|500|
|2|Bob|300|

**Goal:** Transfer $100 from Alice to Bob **safely**.

```SQL
START TRANSACTION;

-- Deduct from Alice
UPDATE accounts
SET balance = balance - 100
WHERE account_id = 1;

-- Add to Bob
UPDATE accounts
SET balance = balance + 100
WHERE account_id = 2;

-- Commit if all went well
COMMIT;

```

✅ After COMMIT:

|account_id|name|balance|
|---|---|---|
|1|Alice|400|
|2|Bob|400|

---

### Step 2: Rollback on Error

```SQL
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;

-- Suppose an error occurs here
-- ROLLBACK to undo deduction
ROLLBACK;

```

✅ Alice’s balance stays at **500**, ensuring **no partial updates**.

---

## ✅ Key Takeaways

- `BEGIN TRANSACTION` / `START TRANSACTION` **groups multiple SQL statements** into one atomic operation.
- Use `COMMIT` to **finalize** changes.
- Use `ROLLBACK` to **undo** changes on error.
- Essential for **financial operations, inventory updates, or multi-step processes**.
- Ensures **ACID compliance** for reliable database operations.