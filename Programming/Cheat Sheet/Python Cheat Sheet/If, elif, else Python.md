---
Created: 2025-08-21T19:29
tags:
  - Control-Flow
---
## What is it?

- **if, elif, else** are conditional statements used to make decisions in code.
- They let your program run different blocks of code based on whether a condition is true or false.

---

## Syntax

```Python
if condition1:
    # block executed if condition1 is True
elif condition2:
    # block executed if condition1 is False and condition2 is True
else:
    # block executed if all above conditions are False
```

---

## How it works

- Python evaluates conditions from top to bottom.
- The first condition that evaluates to True runs its block.
- The rest are skipped.
- If no condition is True, the else block runs (if provided).

---

## Summary Table

|Keyword|Purpose|Condition Checked?|Runs If Condition Is True?|
|---|---|---|---|
|`if`|Tests the first condition|Yes|Yes|
|`elif`|Tests additional conditions (optional)|Yes|Yes|
|`else`|Runs if all previous conditions are False|No|Runs if all above False|

---

## Real-World Examples

### Example 1: Grading System

```Python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: F")
```

Output:

```Plain
Grade: B
```

### Example 2: Weather Check

```Python
temperature = 25

if temperature > 30:
    print("It's hot outside!")
elif temperature > 20:
    print("Nice weather today.")
else:
    print("It's a bit cold.")
```

Output:

```Plain
Nice weather today.
```

### Example 3: User Authentication

```Python
username = "admin"
password = "1234"

if username == "admin" and password == "1234":
    print("Access granted.")
elif username == "admin":
    print("Password incorrect.")
else:
    print("Unknown user.")
```

Output:

```Plain
Access granted.
```

---

## Tips

- You can have multiple `elif` branches.
- `else` is optional.
- Conditions must evaluate to a boolean (`True` or `False`).
- Use logical operators (`and`, `or`, `not`) for complex conditions.

---

## Nested If Example

```Python
age = 20

if age >= 18:
    if age >= 21:
        print("You can drink alcohol.")
    else:
        print("You can vote but not drink alcohol.")
else:
    print("You are too young to vote.")
```

Output:

```Plain
You can vote but not drink alcohol.
```