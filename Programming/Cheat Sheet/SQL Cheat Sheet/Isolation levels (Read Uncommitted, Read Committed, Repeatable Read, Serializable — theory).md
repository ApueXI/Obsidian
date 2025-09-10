---
Created: 2025-09-09T20:12
tags:
  - Transactions-&-Concurrency
---
## 1. Full Explanation

### 🔹 What are Isolation Levels?

- **Isolation levels** define how **concurrent transactions** interact with each other.
- Control **visibility of uncommitted changes** and **prevent anomalies** like dirty reads, non-repeatable reads, and phantom reads.
- Higher isolation usually **increases consistency** but may **reduce concurrency**.

### 🔹 The 4 Standard Isolation Levels

|Isolation Level|Description|Prevented Problems|
|---|---|---|
|**Read Uncommitted**|Transactions can read **uncommitted changes** from other transactions.|Prevents nothing; dirty reads possible.|
|**Read Committed**|Can only read **committed data** from other transactions.|Prevents dirty reads; non-repeatable reads & phantoms possible.|
|**Repeatable Read**|Locks rows read by the transaction until it finishes; ensures **same value** if reread.|Prevents dirty reads and non-repeatable reads; phantoms possible.|
|**Serializable**|Transactions are fully isolated; executed as if **sequentially**, not concurrently.|Prevents dirty reads, non-repeatable reads, and phantom reads; most restrictive.|

---

### 🔹 Key Concepts

1. **Dirty Read** – Reading data **that has been modified but not committed** by another transaction.
2. **Non-Repeatable Read** – Reading the same row **twice** in a transaction returns **different values** because another transaction modified it.
3. **Phantom Read** – A **new row appears** in the result set if another transaction inserts it before your next read.

---

## 2. Summary Table (Quick Reference)

|Level|Can Read Uncommitted Data?|Can Others See Changes Before Commit?|Locks Rows?|Anomalies Prevented|
|---|---|---|---|---|
|**Read Uncommitted**|Yes|Yes|No|None|
|**Read Committed**|No|No|Short-term|Dirty reads|
|**Repeatable Read**|No|No|Row-level|Dirty & non-repeatable reads|
|**Serializable**|No|No|Full table / Range|All (dirty, non-repeatable, phantom)|

---

## 3. Real-World Example

Suppose we have **Accounts table**:

|account_id|name|balance|
|---|---|---|
|1|Alice|500|
|2|Bob|300|

### Example: Dirty Read

- Transaction A: `UPDATE accounts SET balance = 400 WHERE account_id = 1;` (not committed)
- Transaction B: `SELECT balance FROM accounts WHERE account_id = 1;`
- **Read Uncommitted** → sees `400` (dirty read)
- **Read Committed** → sees `500` (no dirty read)

---

### Example: Non-Repeatable Read

- Transaction A: `SELECT balance FROM accounts WHERE account_id = 1;` → sees `500`
- Transaction B: `UPDATE accounts SET balance = 400 WHERE account_id = 1; COMMIT;`
- Transaction A (repeat read): `SELECT balance ...`
- **Read Committed** → sees `400` (non-repeatable read occurs)
- **Repeatable Read** → still sees `500`

---

### Example: Phantom Read

- Transaction A: `SELECT * FROM accounts WHERE balance > 300;` → sees Alice
- Transaction B: `INSERT INTO accounts VALUES (3, 'Charlie', 600); COMMIT;`
- Transaction A (repeat read): `SELECT * ...`
- **Repeatable Read** → still sees only Alice (rows locked)
- **Serializable** → sees only Alice (prevents new rows from appearing)

---

## ✅ Key Takeaways

- **Read Uncommitted** → fastest, dirty reads possible
- **Read Committed** → default in many DBMS, prevents dirty reads
- **Repeatable Read** → prevents dirty & non-repeatable reads, allows phantoms
- **Serializable** → strictest, prevents all anomalies, lowest concurrency
- Choose isolation based on **balance between data consistency and system performance**