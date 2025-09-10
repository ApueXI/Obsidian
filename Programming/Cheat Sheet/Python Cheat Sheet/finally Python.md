---
Created: 2025-08-21T19:29
tags:
  - Exception-Handling
---
## 1. What is the `finally` Block?

- The `finally` block is part of the **try-except-finally** construct.
- It contains code that **always executes**, no matter what happens in the `try` or `except` blocks.
- Typically used for **cleanup actions** like closing files, releasing resources, or resetting states.

---

## 2. Basic Syntax

```Python
try:
    # Code that might raise exceptions
except SomeException:
    # Handle exceptions
finally:
    # Code that runs no matter what
```

---

## 3. Key Points About `finally`

- Executes **after** the `try` and any `except` block(s).
- Executes even if there is a **return**, **break**, or **continue** statement in `try` or `except`.
- Executes even if an **uncaught exception** is raised (before the program terminates).

---

## 4. Why Use `finally`?

- To **release resources** (files, network connections).
- To perform **cleanup** regardless of success or failure.
- To ensure some code runs **no matter what**.

---

## 5. Example: File Handling with `finally`

```Python
try:
    f = open("data.txt", "r")
    data = f.read()
    print(data)
except FileNotFoundError:
    print("File not found!")
finally:
    f.close()  # Always closes the file, even if exception occurs
    print("File closed.")
```

---

## 6. Another Example: `finally` with `return`

```Python
def test_finally():
    try:
        return 1
    finally:
        print("Finally runs even after return")

result = test_finally()
print(result)
```

Output:

```Plain
Finally runs even after return
1
```

---

## Summary Table

|Block|When It Runs|Purpose|
|---|---|---|
|`try`|Always runs first|Code that may raise exceptions|
|`except`|Runs if an exception occurs|Exception handling|
|`finally`|Always runs after `try` and `except` blocks|Cleanup / guaranteed execution|