---
Created: 2025-08-21T19:29
tags:
  - Exception-Handling
---
## 1. What is the `else` Block?

- The `else` block is an **optional** part of the `try-except` structure.
- Code inside `else` runs **only if the** `**try**` **block succeeds without raising any exceptions**.
- Helps separate the **normal execution** from the **exception handling** code, making code clearer.

---

## 2. Basic Syntax

```Python
try:
    # Code that might raise exceptions
except SomeException:
    # Handle exception
else:
    # Runs if no exception was raised in try
```

---

## 3. When to Use `else`?

- Place code that should run **only when no exceptions occur**.
- Keeps `try` block focused on **risky operations**.
- Avoids running code that depends on successful completion of `try` inside the `try` itself.

---

## 4. Example: Using `else` with File Operations

```Python
try:
    f = open("data.txt", "r")
except FileNotFoundError:
    print("File not found!")
else:
    data = f.read()
    print(data)
    f.close()
```

- `else` block runs **only if the file was successfully opened**.
- If the file is missing, `except` handles it, and `else` is skipped.

---

## 5. `try-except-else-finally` Structure

```Python
try:
    # risky code
except SomeException:
    # handle exceptions
else:
    # runs if no exceptions
finally:
    # runs always (cleanup)
```

---

## 6. Real-World Example: Validate Input and Process

```Python
try:
    num = int(input("Enter a number: "))
except ValueError:
    print("That's not a valid number!")
else:
    print(f"You entered {num}, its square is {num**2}.")
```

Output if input is valid:

```Plain
You entered 5, its square is 25.
```

Output if input is invalid:

```Plain
That's not a valid number!
```

---

## Summary Table

|Block|When It Runs|Purpose|
|---|---|---|
|`try`|Always runs first|Code that might raise exceptions|
|`except`|Runs if an exception is raised|Exception handling|
|`else`|Runs only if no exception in `try`|Code that runs on success|
|`finally`|Always runs after `try`, `except`, and `else`|Cleanup / guaranteed execution|