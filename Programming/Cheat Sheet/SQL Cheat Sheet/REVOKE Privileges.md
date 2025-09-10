---
Created: 2025-09-09T20:27
tags:
  - Security-&-Permissins
---
## 1. Full Explanation

### 🔹 What is `REVOKE`?

- `REVOKE` **removes previously granted privileges** from a user or role.
- Essential for **security management**, correcting access errors, or restricting permissions.
- Works on **databases, schemas, tables, and roles**.

---

### 🔹 General Syntax

```SQL
-- Revoke privileges on a table
REVOKE privilege_list
ON table_name
FROM username;

-- Revoke privileges on a schema (PostgreSQL)
REVOKE privilege_list
ON SCHEMA schema_name
FROM username;

-- Revoke privileges on a database
REVOKE ALL PRIVILEGES
ON database_name.*
FROM username;

```

**Notes:**

- `privilege_list` can include: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `REFERENCES`, `EXECUTE`, etc.
- Some DBMS support **roles**: revoke privileges from a role, affecting all users assigned to it.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Revoke table privileges|`REVOKE SELECT, INSERT ON table_name FROM user;`|Removes specific operations|
|Revoke schema privileges|`REVOKE USAGE, CREATE ON SCHEMA schema_name FROM user;`|PostgreSQL example|
|Revoke database privileges|`REVOKE ALL PRIVILEGES ON database_name.* FROM user;`|Removes all access to database|
|Revoke all privileges|`REVOKE ALL PRIVILEGES ON object_name FROM user;`|Can be applied to table, schema, or DB|
|Revoke role privileges|`REVOKE role_name FROM user;`|Removes a role assignment|

---

## 3. Real-World Example

Suppose we have **CompanyDB** with schema `HR`.

### Step 1: Revoke table-level privilege

```SQL
REVOKE INSERT ON HR.Employees FROM hr_user;

```

✅ `hr_user` can no longer **insert new records**, but can still **SELECT or UPDATE**.

### Step 2: Revoke schema-level privileges (PostgreSQL)

```SQL
REVOKE CREATE ON SCHEMA HR FROM hr_user;

```

✅ `hr_user` can no longer **create new tables** in `HR` schema.

### Step 3: Revoke database-level privileges

```SQL
REVOKE ALL PRIVILEGES ON CompanyDB.* FROM temp_user;

```

✅ `temp_user` loses **all access** to the `CompanyDB` database.

### Step 4: Revoke role assignment

```SQL
REVOKE hr_role FROM hr_user;

```

✅ `hr_user` no longer inherits **privileges associated with** `**hr_role**`.

---

## ✅ Key Takeaways

- `**REVOKE**` removes privileges or roles from users or roles.
- Works at **table, schema, database, or role level**.
- Use to **correct access mistakes** or **limit permissions**.
- Always check **dependent objects and permissions** before revoking critical access.
- Works hand-in-hand with **GRANT** to manage database security dynamically.