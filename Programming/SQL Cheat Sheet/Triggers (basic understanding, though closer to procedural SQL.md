---
Created: 2025-09-09T20:34
tags:
  - Optional-Built-in-Extras-(ANSI-SQL-Standard)
---
## 1. Full Explanation

### 🔹 What is a Trigger?

- A **trigger** is a **special stored procedure** that automatically executes when a specific **event occurs** on a table or view.
- Typically used for:
    - **Enforcing business rules**
    - **Automatic auditing/logging**
    - **Validating or modifying data** before/after operations

---

### 🔹 Key Concepts

|Concept|Explanation|
|---|---|
|**Event**|The operation that activates the trigger (`INSERT`, `UPDATE`, `DELETE`)|
|**Timing**|When the trigger fires: `BEFORE` or `AFTER` the event|
|**Level**|Can fire **per row** (`FOR EACH ROW`) or **per statement**|
|**Trigger Body**|Procedural code executed when the trigger fires|
|**NEW / OLD values**|References to **newly inserted/updated** or **old deleted/updated** row values|

---

### 🔹 Basic Syntax (MySQL / PostgreSQL style)

```SQL
CREATE TRIGGER trigger_name
BEFORE INSERT ON Employees
FOR EACH ROW
BEGIN
    -- Procedural logic here
    IF NEW.salary < 30000 THEN
        SET NEW.salary = 30000;  -- enforce minimum salary
    END IF;
END;

```

**Notes:**

- `NEW.column_name` → the value being inserted/updated
- `OLD.column_name` → the value being deleted/updated
- Timing:
    - `BEFORE` → modify values before insertion/update
    - `AFTER` → perform actions after insertion/update

---

### 🔹 Example 1: Auditing Changes

```SQL
CREATE TABLE EmployeeAudit (
    audit_id INT AUTO_INCREMENT PRIMARY KEY,
    employee_id INT,
    old_salary DECIMAL(10,2),
    new_salary DECIMAL(10,2),
    changed_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TRIGGER trg_salary_update
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
    INSERT INTO EmployeeAudit(employee_id, old_salary, new_salary)
    VALUES (OLD.employee_id, OLD.salary, NEW.salary);
END;

```

✅ Automatically logs **salary changes** in a separate table.

---

### 🔹 Example 2: Enforcing Business Rule

```SQL
CREATE TRIGGER trg_min_age
BEFORE INSERT ON Employees
FOR EACH ROW
BEGIN
    IF NEW.age < 18 THEN
        SET NEW.age = 18;  -- minimum age enforcement
    END IF;
END;

```

✅ Ensures **no employee under 18** is inserted.

---

### 🔹 Advantages of Triggers

- Automates **routine validation and auditing**
- Ensures **consistency and business rules enforcement**
- Can **reduce application logic**, centralizing rules in the database

---

### 🔹 Disadvantages

- Can **impact performance** if overused
- Harder to debug compared to application logic
- Logic hidden in triggers may be **non-obvious to developers**

---

### 🔹 Procedural SQL Features Often Used in Triggers

- **IF…ELSE** for conditional logic
- **Loops** for multiple row operations (less common)
- **Variables** to store intermediate calculations
- **INSERT / UPDATE / DELETE statements** for cascading actions

---

## 2. Summary Table (Quick Reference)

|Feature|Syntax / Example|Notes|
|---|---|---|
|Create trigger|`CREATE TRIGGER trg_name BEFORE INSERT ...`|Fires automatically|
|Event types|`INSERT`, `UPDATE`, `DELETE`|Operation that triggers it|
|Timing|`BEFORE`, `AFTER`|When trigger fires|
|Row-level vs Statement-level|`FOR EACH ROW` vs statement-wide|Row-level is most common|
|Accessing values|`NEW.column_name`, `OLD.column_name`|Depends on operation|
|Auditing example|See EmployeeAudit example|Logs changes automatically|

---

### ✅ Key Takeaways

- **Triggers** = automatic procedures triggered by **INSERT, UPDATE, DELETE**
- Can enforce **business rules, auditing, or derived calculations**
- Use **NEW and OLD** to access row values
- **BEFORE triggers** → modify incoming data; **AFTER triggers** → react to changes
- Powerful for **data integrity**, but should be used **judiciously to avoid performance issues**