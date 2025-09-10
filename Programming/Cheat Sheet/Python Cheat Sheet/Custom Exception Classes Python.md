---
Created: 2025-08-21T19:29
tags:
  - Exception-Handling
---
## 1. Why Create Custom Exceptions?

- To **define your own error types** for more meaningful error handling.
- Helps differentiate different error conditions in your application.
- Makes debugging easier and improves code readability.

---

## 2. Basic Custom Exception

A custom exception is just a class that **inherits from** `**Exception**` (or a subclass).

```Python
class MyCustomError(Exception):
    """A custom exception for specific errors."""
    pass

# Usage
raise MyCustomError("Something went wrong!")
```

---

## 3. Adding Extra Information

You can override `__init__` to store extra data.

```Python
class ValidationError(Exception):
    def __init__(self, field, message):
        self.field = field
        self.message = message
        super().__init__(f"[{field}] {message}")

# Usage
raise ValidationError("age", "Age must be positive!")
```

Output:

```Plain
Traceback ...
ValidationError: [age] Age must be positive!
```

---

## 4. Catching Custom Exceptions

```Python
try:
    raise MyCustomError("Something broke!")
except MyCustomError as e:
    print("Handled custom exception:", e)
```

---

## 5. Creating a Hierarchy of Exceptions

You can create a **base exception class** for your module/app, then specialize it:

```Python
class AppError(Exception):
    """Base exception for all app-related errors."""
    pass

class DatabaseError(AppError):
    pass

class NetworkError(AppError):
    pass

try:
    raise NetworkError("Connection lost!")
except AppError as e:  # catches ALL custom errors
    print("App error:", e)
```

✅ Useful when you want **one catch for multiple related errors**.

---

## 6. Best Practices

✅ Always inherit from `Exception` (not `BaseException`, which is reserved for system exit, keyboard interrupts, etc.)

✅ Provide a **clear, descriptive name**

✅ Optionally include **docstrings and custom fields**

---

## Summary Table

|Custom Exception Type|How It Works|
|---|---|
|Basic Custom Exception|`class MyError(Exception): pass`|
|With extra info|Override `__init__` to store fields|
|Hierarchy of exceptions|Have a `BaseError` → `SpecificError` subclasses|
|Catch all related errors|`except BaseError:` catches all child exceptions|

---

## Real-World Example: Validating User Registration

```Python
class RegistrationError(Exception):
    """Base error for registration issues."""
    pass

class UsernameTakenError(RegistrationError):
    def __init__(self, username):
        self.username = username
        super().__init__(f"Username '{username}' is already taken.")

class WeakPasswordError(RegistrationError):
    def __init__(self):
        super().__init__("Password is too weak.")

def register(username, password):
    existing_users = ["alice", "bob"]
    if username in existing_users:
        raise UsernameTakenError(username)
    if len(password) < 6:
        raise WeakPasswordError()
    return "Registration successful!"

try:
    print(register("alice", "123"))
except RegistrationError as e:
    print("Registration failed:", e)
```

Output:

```Plain
Registration failed: Username 'alice' is already taken.
```

✅ **Custom error hierarchy** allows precise control & meaningful error messages.