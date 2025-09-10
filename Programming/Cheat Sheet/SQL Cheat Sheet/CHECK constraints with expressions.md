---
Created: 2025-09-09T20:34
tags:
  - Optional-Built-in-Extras-(ANSI-SQL-Standard)
---
## 1. Full Explanation

### 🔹 What is a `CHECK` Constraint?

- A `CHECK` constraint **limits the values** that can be stored in a column.
- Ensures **data integrity** by enforcing **business rules** at the database level.
- Can be applied **to a single column** or **multiple columns** using expressions.

---

### 🔹 General Syntax

**Single-column CHECK:**

```SQL
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    CONSTRAINT chk_age CHECK (age >= 18)
);

```

✅ Ensures `age` is **18 or older**.

**Multiple-column CHECK:**

```SQL
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    quantity INT,
    price DECIMAL(10,2),
    CONSTRAINT chk_total CHECK (quantity * price <= 10000)
);

```

✅ Ensures **total order value** does not exceed 10,000.

**Inline syntax (column-level):**

```SQL
CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    price DECIMAL(10,2) CHECK (price > 0)
);

```

---

### 🔹 Rules & Notes

1. **Expressions must return TRUE or FALSE**.
2. Cannot reference columns in other tables.
3. CHECK constraints can include:
    - Comparison operators: `=, <>, >, <, >=, <=`
    - Logical operators: `AND, OR, NOT`
    - Functions supported by DBMS: `LENGTH()`, `UPPER()`, etc.
4. Named constraints (`CONSTRAINT name CHECK`) are recommended for **easy modification or deletion**.

---

### 🔹 Alter Table to Add CHECK Constraint

```SQL
ALTER TABLE Employees
ADD CONSTRAINT chk_salary CHECK (salary >= 30000);

```

---

### 🔹 Drop a CHECK Constraint

```SQL
ALTER TABLE Employees
DROP CONSTRAINT chk_salary;

```

**Note:** Some DBMS like MySQL require the **constraint name** to drop it.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Column-level CHECK|`price DECIMAL CHECK (price > 0)`|Applies to single column|
|Table-level CHECK|`CONSTRAINT chk_total CHECK (quantity * price <= 10000)`|Can use multiple columns|
|Add CHECK after creation|`ALTER TABLE ... ADD CONSTRAINT ... CHECK (...)`|Adds new constraint|
|Drop CHECK|`ALTER TABLE ... DROP CONSTRAINT chk_name;`|Remove constraint safely|

---

## 3. Real-World Example

### Employee Table

```SQL
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    salary DECIMAL(10,2),
    CONSTRAINT chk_age CHECK (age >= 18),
    CONSTRAINT chk_salary CHECK (salary >= 30000)
);

```

**Behavior:**

- Insert with `age = 16` → fails.
- Insert with `salary = 25000` → fails.
- Insert with `age = 25` and `salary = 35000` → succeeds.

### Order Table

```SQL
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    quantity INT,
    price DECIMAL(10,2),
    CONSTRAINT chk_total CHECK (quantity * price <= 10000)
);

```

**Behavior:**

- Insert with `quantity = 50` and `price = 300` → fails (50*300=15000 > 10000).

---

## ✅ Key Takeaways

- **CHECK constraints** enforce **business rules at the column or table level**.
- Expressions can be **single-column or multi-column**.
- Use **named constraints** for easy maintenance.
- Helps maintain **data integrity without triggers**.
- Combine with other constraints (`NOT NULL`, `PRIMARY KEY`, `FOREIGN KEY`) for **robust data validation**.