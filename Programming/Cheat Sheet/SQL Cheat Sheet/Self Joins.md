---
Created: 2025-09-09T19:55
tags:
  - Joins
---
## 1. Full Explanation

### 🔹 What is a Self Join?

- A **Self Join** is a join where a table is joined with **itself**.
- Useful for comparing rows **within the same table**.
- Requires **table aliases** to differentiate between the two “instances” of the same table.

### 🔹 General Syntax

```SQL
SELECT a.column1, b.column2
FROM table_name AS a
JOIN table_name AS b
ON a.common_column = b.common_column
WHERE condition;

```

**Notes:**

- Can use **INNER JOIN, LEFT JOIN, or any join type**.
- Often used for **hierarchical data**, such as employees and managers, or comparing related rows.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Basic self join|`FROM employees e1 JOIN employees e2 ON e1.manager_id = e2.employee_id`|Join table with itself|
|Using aliases|`AS e1, AS e2`|Required to differentiate rows|
|Filter rows|`WHERE e1.salary > e2.salary`|Compare within table|
|Combine with aggregate|`GROUP BY e2.department`|Can summarize hierarchical relationships|
|Works with any join type|INNER, LEFT, etc.|Depends on desired result|

---

## 3. Real-World Example

Suppose we have an **Employees table**:

|employee_id|name|manager_id|salary|
|---|---|---|---|
|1|Alice|NULL|100000|
|2|Bob|1|80000|
|3|Charlie|1|90000|
|4|Dave|2|70000|

### Step 1: Get employees with their manager names

```SQL
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id;

```

✅ Returns:

|employee|manager|
|---|---|
|Alice|NULL|
|Bob|Alice|
|Charlie|Alice|
|Dave|Bob|

> Note: Alice has no manager → NULL

### Step 2: Compare salaries with manager

```SQL
SELECT e1.name AS employee, e2.name AS manager, e1.salary, e2.salary AS manager_salary
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id
WHERE e1.salary > e2.salary;

```

✅ Returns:

|employee|manager|salary|manager_salary|
|---|---|---|---|
|Charlie|Alice|90000|100000|

> (Only shows employees earning more than their manager)

---

## ✅ Key Takeaways

- Self Join allows a table to **reference itself**.
- Requires **aliases** for clarity.
- Useful for **hierarchical relationships** (e.g., employee-manager).
- Can be used with **any type of join** and **aggregates**.
- Often combined with **WHERE** to filter relationships within the same table.