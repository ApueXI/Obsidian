---
Created: 2025-09-09T19:49
tags:
  - Basic-Queries-(SELECT)
---
## 1. Full Explanation

### 🔹 What are Logical Operators?

- Logical operators are used in **WHERE clauses** to **combine or negate conditions**.
- They allow more **complex filtering** than single conditions.

### 🔹 Main Logical Operators

|Operator|Description|Example|
|---|---|---|
|`AND`|Both conditions must be true|`WHERE age > 18 AND status = 'active'`|
|`OR`|Either condition is true|`WHERE status = 'active' OR status = 'pending'`|
|`NOT`|Negates a condition|`WHERE NOT status = 'inactive'`|

---

### 🔹 How They Work

1. **AND**

- Only returns rows where **all conditions** are true.
- Precedence: `AND` is evaluated **before OR** unless parentheses are used.

1. **OR**

- Returns rows where **at least one condition** is true.
- Can combine multiple conditions for flexible filtering.

1. **NOT**

- Reverses the result of a condition.
- Can be used with `IN`, `LIKE`, or any comparison.

---

## 2. Real-World Example

Suppose we have a **Users table**:

|user_id|name|age|status|
|---|---|---|---|
|1|Alice|25|active|
|2|Bob|17|inactive|
|3|Charlie|30|pending|
|4|Dave|22|active|
|5|Eve|28|inactive|

### Step 1: Using AND

```SQL
SELECT name
FROM users
WHERE age > 20 AND status = 'active';

```

✅ Returns: Alice, Dave

### Step 2: Using OR

```SQL
SELECT name
FROM users
WHERE status = 'active' OR age < 20;

```

✅ Returns: Alice, Bob, Dave

### Step 3: Using NOT

```SQL
SELECT name
FROM users
WHERE NOT status = 'inactive';

```

✅ Returns: Alice, Charlie, Dave

### Step 4: Combining operators

```SQL
SELECT name
FROM users
WHERE (age > 20 AND status = 'active') OR status = 'pending';

```

✅ Returns: Alice, Charlie, Dave

---

## ✅ Key Takeaways

- `AND` → All conditions must be true.
- `OR` → At least one condition must be true.
- `NOT` → Negates a condition.
- Use **parentheses** to control **operator precedence**.
- Logical operators are essential for **complex queries**.