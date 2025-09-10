---
Created: 2025-06-23T20:20
---
## What is Authentication?

- The process of **verifying who a user is**.
- Confirms user identity by checking credentials (username/password, biometrics, tokens).
- Example: Logging in to a website.

  

## What is Authorization?

- The process of **determining what an authenticated user is allowed to do**.
- Controls access to resources and actions based on user permissions or roles.
- Example: Checking if a user can access admin pages or edit data.

  

## Key Differences

|   |   |   |
|---|---|---|
|Aspect|Authentication|Authorization|
|Purpose|Verify identity|Verify permissions|
|When it occurs|Before authorization|After authentication|
|Checks|User credentials (password, token)|Access rights and privileges|
|Outcome|User is authenticated or not|User is allowed or denied actions|
|Example|Login with username & password|User roles, access control lists|

  

## How They Work Together

1. **User authenticates** (logs in, provides credentials).
2. Server **validates credentials** and creates a session/token.
3. For each request, server **checks authorization** to allow or deny access to specific resources or operations.

  

## Common Authentication Methods

- Password-based login
- OAuth (Google, Facebook login)
- Multi-factor Authentication (MFA)
- Token-based (JWT, API keys)

  

## Common Authorization Methods

- Role-Based Access Control (RBAC)
- Attribute-Based Access Control (ABAC)
- Access Control Lists (ACLs)
- Permission levels (read, write, admin)

  

## Summary Table

|   |   |   |
|---|---|---|
|Feature|Authentication|Authorization|
|Purpose|Identify user|Control user actions|
|Involves|Login credentials|Permissions & roles|
|Happens|Once or at login|On every protected action|
|Example tools|Passport.js, OAuth|Casbin, ACLs, RBAC|