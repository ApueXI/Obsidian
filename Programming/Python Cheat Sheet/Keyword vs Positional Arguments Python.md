---
Created: 2025-08-21T19:29
tags:
  - Function
---
## 1. Positional Arguments

- **Passed in order** they appear in the function definition.
- The function **matches them by position**.

```Python
def greet(first, second):
    print(f"Hello {first} and {second}!")

greet("Alice", "Bob")  # first="Alice", second="Bob"
```

✅ **Good for short/simple functions**

❌ **Order matters** → if you swap, the meaning changes.

---

## 2. Keyword Arguments

- Passed as `name=value` pairs.
- **Order doesn’t matter** since they are matched by name.

```Python
def greet(first, second):
    print(f"Hello {first} and {second}!")

greet(second="Bob", first="Alice")  # Order doesn’t matter
```

✅ **More readable** and **order-independent**

✅ Can combine with positional arguments

❌ Slightly longer to type

---

## 3. Mixed Arguments

- Positional arguments **must come first**, then keyword arguments.

```Python
def greet(first, second, greeting="Hello"):
    print(f"{greeting}, {first} and {second}!")

greet("Alice", "Bob", greeting="Hi")  # Mixed usage
```

❌ **Invalid:**

```Python
greet(first="Alice", "Bob")  # ❌ SyntaxError
```

---

## 4. Special Parameters

Python 3 allows enforcing **only-positional** or **only-keyword** parameters:

```Python
def func(a, b, /, c, *, d):
    # a, b → positional-only
    # c → can be either
    # d → keyword-only
    pass
```

✅ `**/**` → all before are positional-only

✅ `*****` → all after are keyword-only

---

## Summary Table

|Argument Type|Example Call|Matched By|Order Matters?|
|---|---|---|---|
|**Positional**|`greet("Alice", "Bob")`|Position|✅ Yes|
|**Keyword**|`greet(first="Alice", second="Bob")`|Name|❌ No|
|**Mixed**|`greet("Alice", second="Bob")`|Position + Name|✅ Only for first|
|**Positional-only**|`func(1, 2)` (defined with `/`)|Position|✅ Yes|
|**Keyword-only**|`func(d=4)` (defined with `*`)|Name|❌ No|

---

## Real-World Example: Email Sender

```Python
def send_email(to, subject, body, priority="Normal"):
    print(f"Sending email to {to}")
    print(f"Subject: {subject}")
    print(f"Body: {body}")
    print(f"Priority: {priority}")

# Positional
send_email("user@example.com", "Welcome", "Thanks for signing up!")

# Keyword
send_email(to="user@example.com", body="Hi there!", subject="Hello!", priority="High")

# Mixed
send_email("user@example.com", "Reminder", body="Meeting at 5 PM", priority="Urgent")
```

✅ Flexible calling style

✅ More readable with keywords when many arguments