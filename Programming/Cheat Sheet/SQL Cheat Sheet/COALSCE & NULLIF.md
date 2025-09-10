---
Created: 2025-09-09T20:21
tags:
  - Advance-Querying
---
## 1. Full Explanation

### 🔹 `COALESCE`

- Returns the **first non-NULL value** in a list of expressions.
- Useful for **handling NULLs** and providing **default values**.

**Syntax:**

```SQL
COALESCE(expr1, expr2, ..., exprN)

```

**Notes:**

- Evaluates **left to right** and stops at the first non-NULL value.
- Commonly used in **SELECT, INSERT, and UPDATE** statements.

---

### 🔹 `NULLIF`

- Compares **two expressions**; returns **NULL if they are equal**, otherwise returns the **first expression**.
- Useful to **avoid divide-by-zero errors** or flag specific values as NULL.

**Syntax:**

```SQL
NULLIF(expr1, expr2)

```

**Notes:**

- Returns `NULL` if `expr1 = expr2`; otherwise returns `expr1`.
- Often used in calculations or conditional logic.

---

## 2. Summary Table (Quick Reference)

|Function|Syntax|Returns|Use Case|
|---|---|---|---|
|`COALESCE`|`COALESCE(expr1, expr2, ...)`|First non-NULL value|Provide default values for NULLs|
|`NULLIF`|`NULLIF(expr1, expr2)`|NULL if equal, else expr1|Avoid errors or treat specific values as NULL|

---

## 3. Real-World Example

Suppose we have **Employees table**:

|employee_id|name|bonus|
|---|---|---|
|1|Alice|NULL|
|2|Bob|500|
|3|Charlie|0|

---

### Step 1: Use `COALESCE` to provide default bonus

```SQL
SELECT name,
       COALESCE(bonus, 100) AS bonus_amount
FROM employees;

```

✅ Returns:

|name|bonus_amount|
|---|---|
|Alice|100|
|Bob|500|
|Charlie|0|

> Alice’s NULL bonus replaced with 100.

---

### Step 2: Use `NULLIF` to handle zero bonus

```SQL
SELECT name,
       NULLIF(bonus, 0) AS bonus_value
FROM employees;

```

✅ Returns:

|name|bonus_value|
|---|---|
|Alice|NULL|
|Bob|500|
|Charlie|NULL|

> Charlie’s 0 treated as NULL, can prevent divide-by-zero or special handling.

---

### Step 3: Combine `COALESCE` & `NULLIF`

```SQL
SELECT name,
       COALESCE(NULLIF(bonus, 0), 100) AS adjusted_bonus
FROM employees;

```

✅ Returns:

|name|adjusted_bonus|
|---|---|
|Alice|100|
|Bob|500|
|Charlie|100|

> Treats NULL and 0 as default 100, while keeping valid bonuses intact.

---

## ✅ Key Takeaways

- `**COALESCE**` → provides a **fallback for NULL values**.
- `**NULLIF**` → **returns NULL when two values are equal**, useful for special cases.
- Can be **combined** to handle **NULLs, defaults, and special values** cleanly.
- Essential for **data cleaning, conditional calculations, and safe arithmetic**.