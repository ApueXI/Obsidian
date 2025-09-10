---
Created: 2025-08-21T19:29
tags:
  - Exception-Handling
---
## 1. What is Exception Handling?

- **Exceptions** are errors detected during execution (e.g., dividing by zero, file not found).
- Use `try` and `except` blocks to **catch and handle exceptions gracefully** without crashing the program.

---

## 2. Basic Syntax

```Python
try:
    # code that might raise an exception
except SomeException:
    # code to handle the exception
```

---

## 3. Catching Multiple Exceptions

```Python
try:
    # risky code
except (ValueError, TypeError):
    # handle either ValueError or TypeError
```

---

## 4. Catching All Exceptions (Not Recommended Unless Needed)

```Python
try:
    # risky code
except Exception as e:
    print("Error:", e)
```

---

## 5. Using `else` and `finally`

```Python
try:
    # risky code
except Exception:
    # handle exceptions
else:
    # runs if no exceptions
finally:
    # always runs, even if exception occurs
```

- `else` block runs only if `try` succeeds
- `finally` block runs no matter what (good for cleanup)

---

## 6. Raising Exceptions

```Python
raise ValueError("Invalid input")
```

You can **raise** exceptions yourself to signal errors.

---

## 7. Real-World Example: Handling File Reading Errors

```Python
try:
    with open("data.txt") as f:
        content = f.read()
except FileNotFoundError:
    print("File not found.")
except IOError:
    print("Error reading file.")
else:
    print("File read successfully.")
finally:
    print("Execution finished.")
```

---

## Summary Table

|Keyword|Purpose|Example|
|---|---|---|
|`try`|Block of code to test for exceptions|`try: x = 1/0`|
|`except`|Handles exceptions raised in try block|`except ZeroDivisionError:`|
|`else`|Runs if no exceptions in try|`else: print("No errors")`|
|`finally`|Runs regardless of exceptions|`finally: print("Cleanup")`|
|`raise`|Raises an exception manually|`raise ValueError("Bad input")`|