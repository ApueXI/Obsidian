---
Created: 2025-09-09T20:29
tags:
  - Normalization-&-Database-Design
---
## 1. Full Explanation

### 🔹 What is Normalization?

- **Normalization** is the process of **organizing a database** to reduce **redundancy** and **improve data integrity**.
- Done in **normal forms**: 1NF, 2NF, 3NF, BCNF, etc.
- Helps prevent **update, insert, and delete anomalies**.

---

### 🔹 1NF – First Normal Form

**Rule:**

- Each column contains **atomic (indivisible) values**.
- Each row is **unique**.

**Key Points:**

- No repeating groups or arrays in a column.
- Primary key ensures uniqueness.

**Example:**

|StudentID|Name|Courses|
|---|---|---|
|1|Alice|Math, English|

**After 1NF:**

|StudentID|Name|Course|
|---|---|---|
|1|Alice|Math|
|1|Alice|English|

---

### 🔹 2NF – Second Normal Form

**Rule:**

- Must be in **1NF**.
- **No partial dependency**: every non-key column must depend on the **entire primary key** (only matters for **composite keys**).

**Example:**

|StudentID|CourseID|StudentName|CourseName|
|---|---|---|---|

- `StudentName` depends only on `StudentID` → partial dependency.

**After 2NF:**

**Students Table:**

|StudentID|StudentName|
|---|---|

**Courses Table:**

|CourseID|CourseName|
|---|---|

**Enrollment Table:**

|StudentID|CourseID|
|---|---|

---

### 🔹 3NF – Third Normal Form

**Rule:**

- Must be in **2NF**.
- **No transitive dependency**: non-key columns cannot depend on other non-key columns.

**Example:**

|StudentID|StudentName|DeptID|DeptName|
|---|---|---|---|

- `DeptName` depends on `DeptID`, not `StudentID` → transitive dependency.

**After 3NF:**

**Students Table:**

|StudentID|StudentName|DeptID|
|---|---|---|

**Departments Table:**

|DeptID|DeptName|
|---|---|

---

### 🔹 BCNF – Boyce-Codd Normal Form

**Rule:**

- Must be in **3NF**.
- **Every determinant** must be a candidate key.
- Handles **special cases where 3NF fails** due to overlapping candidate keys.

**Example:**

|Teacher|Subject|Room|
|---|---|---|

- Suppose **Room → Subject** and **Teacher → Room**,
- 3NF may still have anomalies.

**After BCNF:**

**TeacherRoom Table:**

|Teacher|Room|
|---|---|

**RoomSubject Table:**

|Room|Subject|
|---|---|

✅ Ensures **no redundancy and no anomalies**.

---

## 2. Summary Table (Quick Reference)

|Normal Form|Requirement|Key Focus|
|---|---|---|
|1NF|Atomic values, unique rows|Eliminate repeating groups|
|2NF|1NF + no partial dependency (for composite keys)|Eliminate partial dependency|
|3NF|2NF + no transitive dependency|Eliminate transitive dependency|
|BCNF|3NF + every determinant is a candidate key|Resolve anomalies not handled by 3NF|

---

## 3. Real-World Example

**Raw Table:**

|StudentID|StudentName|DeptID|DeptName|CourseID|CourseName|
|---|---|---|---|---|---|

**Step 1 – 1NF:** Separate multi-valued courses into rows.

**Step 2 – 2NF:** Split tables to remove partial dependencies (Students, Courses, Enrollment).

**Step 3 – 3NF:** Remove transitive dependencies (Students → Departments).

**Step 4 – BCNF:** Ensure all determinants are candidate keys (Teacher → Room → Subject case).

---

## ✅ Key Takeaways

- **Normalization** reduces redundancy, improves data integrity, and prevents anomalies.
- **1NF** → atomic values
- **2NF** → no partial dependency
- **3NF** → no transitive dependency
- **BCNF** → all determinants are candidate keys
- Use **BCNF** when designing **highly reliable, complex databases**.