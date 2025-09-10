---
Created: 2025-09-09T20:18
tags:
  - Indexes
---
## 1. Full Explanation

### 🔹 What is a Clustered Index?

- A **clustered index** determines the **physical order of data** in the table.
- **Only one clustered index** is allowed per table.
- Table data is **stored in the same order** as the index.
- Often created automatically on **primary key columns**.
- **Best for range queries** because rows are physically sorted.

### 🔹 What is a Non-Clustered Index?

- A **non-clustered index** is a separate structure from the table data.
- **Multiple non-clustered indexes** can exist on a table.
- Contains **pointers (row locators)** to the actual data rows.
- Good for **columns frequently used in WHERE, JOIN, or ORDER BY**.

---

### 🔹 Key Differences

|Feature|Clustered Index|Non-Clustered Index|
|---|---|---|
|**Data storage**|Table data physically sorted|Table data stored separately|
|**Number per table**|1|Many|
|**Speed**|Faster for range queries|Faster for selective searches|
|**Primary key**|Usually created automatically|Can be created on any column|
|**Pointer to data**|Not needed (data is in index)|Uses pointers to actual rows|
|**Impact on INSERT/UPDATE/DELETE**|Slower for heavy writes|Less impact, but index must update|

---

## 2. Real-World Analogy

- **Clustered Index:** A **phone book sorted by last name** — the data (names) themselves are physically ordered.
- **Non-Clustered Index:** An **index card that points to pages in a book** — separate structure, points to the actual location.

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|5000|
|2|Bob|IT|6000|
|3|Charlie|IT|5500|

### Step 1: Clustered index on `employee_id`

```SQL
CREATE CLUSTERED INDEX idx_emp_id
ON employees(employee_id);

```

✅ Data is stored in **employee_id order** (1, 2, 3).

---

### Step 2: Non-Clustered index on `department`

```SQL
CREATE NONCLUSTERED INDEX idx_department
ON employees(department);

```

✅ SQL can **quickly find rows in a department** without scanning the entire table.

---

## ✅ Key Takeaways

- **Clustered index:** physically sorts table data; 1 per table; fast for range queries.
- **Non-clustered index:** separate structure; multiple allowed; fast for selective queries.
- Use **clustered index** for **primary keys or range-heavy queries**.
- Use **non-clustered index** for **frequent lookups, filters, joins, or orderings**.