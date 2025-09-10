---
Created: 2025-09-09T20:29
tags:
  - Normalization-&-Database-Design
---
## 1. Full Explanation

### 🔹 What is Referential Integrity?

- **Referential integrity** ensures that **relationships between tables remain consistent**.
- A **foreign key** in one table must **match a primary key** in another table (or be `NULL`).
- Prevents **orphaned records** and maintains **data correctness** across related tables.

---

### 🔹 How Referential Integrity Works

1. **Parent Table** – table containing the **primary key**.
2. **Child Table** – table containing the **foreign key** referencing the parent.
3. **Rules enforced by DBMS**:
    - You **cannot insert a foreign key value** that does not exist in the parent table.
    - You can **cascade updates/deletes** or restrict them to maintain integrity.

---

### 🔹 Syntax

```SQL
-- Create parent table
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(50)
);

-- Create child table with foreign key
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    DeptID INT,
    CONSTRAINT fk_dept FOREIGN KEY (DeptID)
        REFERENCES Departments(DeptID)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);

```

**Notes:**

- `ON DELETE CASCADE` → deleting a department automatically deletes all employees in it.
- `ON UPDATE CASCADE` → updating a department ID updates all referencing foreign keys.
- Alternatives: `SET NULL`, `NO ACTION`, `RESTRICT`.

---

## 2. Foreign Key Actions (Quick Reference)

|Action|Description|
|---|---|
|`CASCADE`|Propagate changes (delete/update) to child table|
|`SET NULL`|Set foreign key to NULL if parent is deleted/updated|
|`NO ACTION` / `RESTRICT`|Prevent action if child rows exist|
|Default (DBMS-dependent)|Usually same as `RESTRICT` or `NO ACTION`|

---

## 3. Summary Table (Parent vs Child)

|Feature|Parent Table|Child Table|
|---|---|---|
|Key|Primary Key|Foreign Key|
|Responsible for|Ensuring referenced value exists|Refers to parent key|
|Referential Integrity|Defines the constraint|Must comply with parent table|
|Example|Departments.DeptID|Employees.DeptID|

---

## 4. Real-World Example

**Departments Table (Parent):**

|DeptID|DeptName|
|---|---|
|1|HR|
|2|IT|

**Employees Table (Child):**

|EmployeeID|Name|DeptID|
|---|---|---|
|101|Alice|1|
|102|Bob|2|

**Behavior:**

- Trying to insert an employee with `DeptID = 3` → **fails** (no such department).
- Deleting department `2` (IT) → **Bob is also deleted** if `ON DELETE CASCADE`.

---

## ✅ Key Takeaways

- **Referential integrity** maintains **data consistency across related tables**.
- Implemented using **foreign keys** that reference primary keys.
- **ON DELETE / ON UPDATE** actions define how changes propagate.
- Essential for **preventing orphaned records and ensuring relational accuracy**.
- Best practice: combine **referential integrity with indexes** on foreign keys for performance.