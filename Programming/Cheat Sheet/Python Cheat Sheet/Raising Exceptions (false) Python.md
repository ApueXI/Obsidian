---
Created: 2025-08-21T19:29
tags:
  - Exception-Handling
---
## 1. What Does _Raising an Exception_ Mean?

- **Raising an exception** means **manually signaling an error** in your program.
- It immediately **stops normal execution** and looks for an `except` block to handle it.
- Syntax:

```Python
raise ExceptionType("optional error message")
```

---

## 2. Basic Example

```Python
def divide(a, b):
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero!")  # Raise built-in exception
    return a / b

try:
    result = divide(10, 0)
except ZeroDivisionError as e:
    print("Error:", e)
```

Output:

```Plain
Error: Cannot divide by zero!
```

---

## 3. Raising a _False/Custom Condition_

Sometimes you want to **raise an exception when a condition is false**:

```Python
x = -5
if x < 0:
    raise ValueError("x must not be negative!")  # custom validation
```

Or using **assert** (a quick way to raise AssertionError if condition is false):

```Python
assert x >= 0, "x must be non-negative"
```

If `x` is negative → `AssertionError: x must be non-negative`

---

## 4. Re-Raising Exceptions

Inside an `except`, you can **re-raise** the same exception:

```Python
try:
    int("abc")
except ValueError:
    print("Handling, then re-raising...")
    raise  # Re-raise the original exception
```

---

## 5. Raising Custom Exceptions

You can define your own exception class:

```Python
class NegativeNumberError(Exception):
    pass

def check_positive(n):
    if n < 0:
        raise NegativeNumberError("Negative numbers not allowed!")
    return n

try:
    check_positive(-10)
except NegativeNumberError as e:
    print("Custom error:", e)
```

Output:

```Plain
Custom error: Negative numbers not allowed!
```

---

## Summary Table

|Action|Syntax/Example|Description|
|---|---|---|
|Raise built-in exception|`raise ValueError("Invalid")`|Manually throw error|
|Raise based on condition|`if x < 0: raise ValueError(...)`|Conditional validation|
|Raise AssertionError|`assert x > 0, "Must be > 0"`|Quick check|
|Re-raise current exception|`raise` (inside `except`)|Re-throw same error|
|Custom exception class|`class MyError(Exception): pass`|Define your own|

---

## Real-World Example: Validating User Input

```Python
def get_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative!")
    if age > 120:
        raise ValueError("Unrealistic age!")
    return age

try:
    user_age = get_age(-5)
except ValueError as e:
    print("Invalid input:", e)
```

Output:

```Plain
Invalid input: Age cannot be negative!
```

✅ Helps enforce **data integrity** and **fail fast** when invalid conditions occur.