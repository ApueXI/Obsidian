---
Created: 2025-09-09T20:22
tags:
  - Advance-Querying
---
## 1. Full Explanation

### 🔹 What are Window Functions?

- Window functions perform **calculations across a set of rows related to the current row**.
- Unlike aggregate functions, they **do not collapse rows**; each row retains its identity.
- Useful for **ranking, running totals, moving averages, percentiles, and more**.
- Uses `OVER()` clause to define the **window of rows**.

---

### 🔹 General Syntax

```SQL
-- Basic form
function_name(column) OVER (
    [PARTITION BY column1, column2]  -- optional grouping within the window
    [ORDER BY column3]                -- optional ordering within the window
    [ROWS BETWEEN ...]                -- optional row range
)

```

**Notes:**

- `PARTITION BY` → divides rows into groups (like GROUP BY but does not collapse rows).
- `ORDER BY` → defines the order for ranking or running totals.
- `ROWS BETWEEN` → defines **frame of rows** for aggregate calculations (optional).

---

## 2. Common Window Functions

|Function|Purpose|Example|
|---|---|---|
|`ROW_NUMBER()`|Assigns sequential numbers to rows in a partition|`ROW_NUMBER() OVER(PARTITION BY department ORDER BY salary DESC)`|
|`RANK()`|Assigns rank; ties get same rank, skips next ranks|`RANK() OVER(ORDER BY salary DESC)`|
|`DENSE_RANK()`|Like RANK, but no gaps for ties|`DENSE_RANK() OVER(ORDER BY salary DESC)`|
|`NTILE(n)`|Divides rows into n buckets|`NTILE(4) OVER(ORDER BY salary)`|
|`SUM()`|Running total over window|`SUM(salary) OVER(ORDER BY salary)`|
|`AVG()`|Moving average over window|`AVG(salary) OVER(PARTITION BY department ORDER BY salary ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING)`|
|`LEAD()`|Access next row’s value|`LEAD(salary,1) OVER(ORDER BY salary)`|
|`LAG()`|Access previous row’s value|`LAG(salary,1) OVER(ORDER BY salary)`|
|`FIRST_VALUE()`|First value in the window|`FIRST_VALUE(salary) OVER(PARTITION BY department ORDER BY salary)`|
|`LAST_VALUE()`|Last value in the window|`LAST_VALUE(salary) OVER(PARTITION BY department ORDER BY salary ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING)`|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5000|
|2|Bob|IT|6000|
|3|Charlie|IT|5500|
|4|David|HR|4500|

---

### Step 1: Assign row numbers by department

```SQL
SELECT name, department, salary,
       ROW_NUMBER() OVER(PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employees;

```

✅ Returns:

|name|department|salary|row_num|
|---|---|---|---|
|Alice|HR|5000|1|
|David|HR|4500|2|
|Bob|IT|6000|1|
|Charlie|IT|5500|2|

---

### Step 2: Calculate running total of salary

```SQL
SELECT name, salary,
       SUM(salary) OVER(ORDER BY salary) AS running_total
FROM employees;

```

✅ Returns:

|name|salary|running_total|
|---|---|---|
|David|4500|4500|
|Alice|5000|9500|
|Charlie|5500|15000|
|Bob|6000|21000|

---

### Step 3: Compare with previous row using LAG

```SQL
SELECT name, salary,
       LAG(salary,1) OVER(ORDER BY salary) AS prev_salary
FROM employees;

```

✅ Returns:

|name|salary|prev_salary|
|---|---|---|
|David|4500|NULL|
|Alice|5000|4500|
|Charlie|5500|5000|
|Bob|6000|5500|

---

## ✅ Key Takeaways

- **Window functions** perform calculations **without collapsing rows**.
- `**OVER()**` **clause** defines partitioning, ordering, and row frames.
- Common uses: **ranking, running totals, moving averages, lead/lag comparisons**.
- Very powerful for **analytics, reporting, and complex queries**.