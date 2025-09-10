---
Created: 2025-09-09T20:26
tags:
  - Security-&-Permissins
---
## 1. Full Explanation

### 🔹 What is `CREATE USER`?

- `CREATE USER` is used to **create a new database user**.
- A user can **log in**, **own objects**, and **be granted permissions** on databases or schemas.
- Users are essential for **security, access control, and auditing**.

---

### 🔹 General Syntax

**Basic syntax:**

```SQL
-- Create a simple user with a password
CREATE USER username IDENTIFIED BY 'password';

```

**SQL Server syntax:**

```SQL
-- Create login at server level
CREATE LOGIN username WITH PASSWORD = 'password';

-- Create database user mapped to login
CREATE USER username FOR LOGIN username;

```

**Notes:**

- Syntax varies between DBMS: MySQL, PostgreSQL, SQL Server, Oracle have slight differences.
- After creating a user, you typically **grant permissions** to allow access to databases, schemas, or tables.

---

### 🔹 Granting Permissions

```SQL
-- Grant all privileges on a database (MySQL/PostgreSQL)
GRANT ALL PRIVILEGES ON database_name.* TO 'username';

-- Grant schema-specific permissions (PostgreSQL)
GRANT SELECT, INSERT ON SCHEMA schema_name TO username;

-- Grant table-specific permissions
GRANT SELECT, UPDATE ON table_name TO username;

```

✅ Proper permission management ensures **security and controlled access**.

---

## 2. Summary Table (Quick Reference)

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create user (MySQL/PostgreSQL)|`CREATE USER 'user' IDENTIFIED BY 'password';`|Basic login credentials|
|Create login & user (SQL Server)|`CREATE LOGIN username WITH PASSWORD='pass'; CREATE USER username FOR LOGIN username;`|Two-step process in SQL Server|
|Grant database permissions|`GRANT ALL PRIVILEGES ON db_name.* TO 'user';`|Full access to database|
|Grant schema permissions|`GRANT SELECT, INSERT ON SCHEMA schema_name TO user;`|Restrict access to specific schema|
|Grant table permissions|`GRANT SELECT, UPDATE ON table_name TO user;`|Fine-grained control|

---

## 3. Real-World Example

### Step 1: Create a user in MySQL

```SQL
CREATE USER 'hr_user' IDENTIFIED BY 'StrongPass123';

```

### Step 2: Grant access to HR schema

```SQL
GRANT SELECT, INSERT, UPDATE ON HR.* TO 'hr_user';

```

### Step 3: Verify access

```SQL
-- Log in as hr_user and query table
SELECT * FROM HR.Employees;

```

✅ `hr_user` can only access **HR schema**, not other schemas like Sales.

---

## ✅ Key Takeaways

- `CREATE USER` adds a **new login/user** to the database.
- Permissions are **not automatic**; must be **granted explicitly**.
- Use for **security, modular access, and auditing**.
- Always follow **principle of least privilege**: give users only the access they need.