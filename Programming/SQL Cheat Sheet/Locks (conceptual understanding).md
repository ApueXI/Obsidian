---
Created: 2025-09-09T20:12
tags:
  - Transactions-&-Concurrency
---
## 1. Full Explanation

### 🔹 What is a Lock?

- A **lock** is a mechanism that **controls concurrent access** to database resources (tables, rows, pages) to ensure **data consistency and integrity**.
- Locks prevent **conflicts** when multiple transactions try to **read/write the same data simultaneously**.
- Locks are used to implement **transaction isolation levels** and prevent anomalies like dirty reads, non-repeatable reads, and phantom reads.

---

### 🔹 Types of Locks

|Lock Type|Description|Typical Use Case|
|---|---|---|
|**Shared Lock (S)**|Multiple transactions can **read** a resource simultaneously, but **cannot write**|Reading data|
|**Exclusive Lock (X)**|Only one transaction can **read and write** a resource; blocks others from reading/writing|Updating or deleting rows|
|**Update Lock (U)**|Special lock to **prevent deadlocks** when a resource may be upgraded from read to write|Preparing to update|
|**Intent Lock (IS, IX)**|Signals that a transaction **intends to acquire locks** on lower-level resources (row/page)|SQL Server internal management|
|**Schema Lock**|Prevents schema changes while queries are running|ALTER TABLE, DROP TABLE|
|**Page/Table Lock**|Locks an entire **page or table**, not individual rows|Large operations, batch updates|

---

### 🔹 Conceptual Principles

1. **Lock Granularity**
    - **Row-level locks** → high concurrency, more overhead.
    - **Table-level locks** → less overhead, lower concurrency.
2. **Lock Modes**
    - **Shared (read)** → multiple transactions can read.
    - **Exclusive (write)** → only one transaction can read/write.
3. **Deadlocks**
    - Occur when two or more transactions **wait indefinitely** for each other’s locks.
    - DBMS detects deadlocks and usually **rolls back one transaction** to resolve it.
4. **Lock Duration**
    - Depends on **transaction isolation level** and **DBMS settings**.
    - Higher isolation levels (e.g., Serializable) → locks held longer → lower concurrency.

---

## 2. Real-World Analogy

- **Library analogy:**
    - Shared lock = multiple students can **read the same book** at the same time.
    - Exclusive lock = only one student can **write notes in the book**, others must wait.
    - Deadlock = two students trying to exchange books **but both are holding the other’s book** → stuck.

---

## 3. Key Takeaways

- Locks ensure **data consistency and integrity** during concurrent transactions.
- **Shared locks** allow simultaneous reads; **exclusive locks** prevent others from reading/writing.
- **Granularity** (row vs table) affects **concurrency and performance**.
- **Deadlocks** are a risk; DBMS usually resolves them automatically.
- Locks are the **underlying mechanism** for implementing transaction isolation levels.