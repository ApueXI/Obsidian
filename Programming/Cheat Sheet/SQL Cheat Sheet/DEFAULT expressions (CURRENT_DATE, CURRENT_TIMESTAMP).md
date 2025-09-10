---
Created: 2025-09-09T20:34
tags:
  - Optional-Built-in-Extras-(ANSI-SQL-Standard)
---
## 1. Full Explanation

### 🔹 What is a `DEFAULT` Expression?

- The `DEFAULT` constraint **automatically assigns a value** to a column if no value is provided during an `INSERT`.
- Can be a **constant value** or an **expression/function**.
- Ensures **data completeness and consistency** without manual input.

---

### 🔹 Common Usage

1. **Constant values**

```SQL
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    status VARCHAR(10) DEFAULT 'Active'
);

```

✅ If `status` is not provided, it defaults to `'Active'`.

1. **Current date / time**

```SQL
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE DEFAULT CURRENT_DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

```

- `CURRENT_DATE` → today's date
- `CURRENT_TIMESTAMP` → current date **and time**

1. **Numeric default**

```SQL
CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    stock INT DEFAULT 0
);

```

✅ Ensures `stock` defaults to `0` if not specified.

---

### 🔹 Alter Table to Add Default

```SQL
ALTER TABLE Employees
ALTER COLUMN status SET DEFAULT 'Active';

```

### 🔹 Drop Default

```SQL
ALTER TABLE Employees
ALTER COLUMN status DROP DEFAULT;

```

**Notes:** Syntax may vary slightly between DBMS (MySQL, PostgreSQL, SQL Server, Oracle).

---

## 2. Summary Table (Quick Reference)

|Feature|Syntax / Example|Notes|
|---|---|---|
|Constant default|`status VARCHAR DEFAULT 'Active'`|Assign fixed value|
|Current date default|`order_date DATE DEFAULT CURRENT_DATE`|Assign today’s date automatically|
|Current timestamp default|`created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP`|Assign current date and time|
|Numeric default|`stock INT DEFAULT 0`|Useful for counters or quantities|
|Add default after creation|`ALTER TABLE ... ALTER COLUMN ... SET DEFAULT`|Modifies existing table|
|Remove default|`ALTER TABLE ... ALTER COLUMN ... DROP DEFAULT`|Removes default constraint|

---

## 3. Real-World Example

```SQL
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE DEFAULT CURRENT_DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(20) DEFAULT 'Pending'
);

```

**Behavior:**

|order_id|customer_id|order_date|created_at|status|
|---|---|---|---|---|
|1|101|2025-09-09|2025-09-09 19:00:00|Pending|

- No need to specify `order_date`, `created_at`, or `status` during insertion; they take **default values automatically**.

---

## ✅ Key Takeaways

- **DEFAULT expressions** automatically fill in **missing column values**.
- Can use **constants, numeric values, or built-in functions** like `CURRENT_DATE` and `CURRENT_TIMESTAMP`.
- Ensures **data consistency** and reduces manual errors.
- Works best for **timestamps, status fields, counters, or optional columns**.