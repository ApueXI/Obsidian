---
Created: 2025-09-09T20:27
tags:
  - Security-&-Permissins
---
## 1. Full Explanation

### 🔹 What is `GRANT`?

- `GRANT` is used to **give privileges to users or roles** in a database.
- Privileges determine **what operations a user can perform**: SELECT, INSERT, UPDATE, DELETE, EXECUTE, etc.
- Essential for **security and access control**.

---

### 🔹 General Syntax

```SQL
-- Grant privileges on a database
GRANT privilege_list
ON database_name.*
TO 'username';

-- Grant privileges on a schema (PostgreSQL)
GRANT privilege_list
ON SCHEMA schema_name
TO username;

-- Grant privileges on a table
GRANT privilege_list
ON table_name
TO username;

-- Grant all privileges
GRANT ALL PRIVILEGES
ON object_name
TO username;

```

**Notes:**

- `privilege_list` can include: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `REFERENCES`, `EXECUTE`, etc.
- Some DBMS support **roles**: assign privileges to a role and then grant role to user.

---

### 🔹 Revoke Privileges

```SQL
REVOKE privilege_list
ON object_name
FROM username;

```

✅ Allows **removing previously granted privileges**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Grant table privileges|`GRANT SELECT, INSERT ON table_name TO user;`|Gives access to specific operations|
|Grant schema privileges|`GRANT USAGE, CREATE ON SCHEMA schema_name TO user;`|DBMS-specific (PostgreSQL example)|
|Grant database privileges|`GRANT ALL PRIVILEGES ON database_name.* TO user;`|Full access to database|
|Grant all privileges|`GRANT ALL PRIVILEGES ON object_name TO user;`|Gives all possible permissions|
|Revoke privileges|`REVOKE SELECT ON table_name FROM user;`|Removes specific privileges|

---

## 3. Real-World Example

Suppose we have **CompanyDB** with schema `HR`.

### Step 1: Grant table-level privileges

```SQL
GRANT SELECT, INSERT, UPDATE ON HR.Employees TO hr_user;

```

✅ `hr_user` can **read, add, and update employee data** but cannot delete.

### Step 2: Grant schema-level privileges (PostgreSQL example)

```SQL
GRANT USAGE, CREATE ON SCHEMA HR TO hr_user;

```

✅ `hr_user` can **use the HR schema** and **create new tables** inside it.

### Step 3: Grant full privileges on database

```SQL
GRANT ALL PRIVILEGES ON CompanyDB.* TO admin_user;

```

✅ `admin_user` can perform **any operation on the database**.

### Step 4: Revoke privileges

```SQL
REVOKE INSERT ON HR.Employees FROM hr_user;

```

✅ `hr_user` can no longer **insert new records**, but can still SELECT or UPDATE.

---

## ✅ Key Takeaways

- `**GRANT**` controls **who can do what** in the database.
- Privileges can be applied to **databases, schemas, tables, or roles**.
- **Use roles** to simplify permissions management for multiple users.
- **Principle of least privilege**: give only necessary access.
- Combine with **REVOKE** to modify access dynamically.