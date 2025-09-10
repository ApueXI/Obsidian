---
Created: 2025-08-21T19:29
tags:
  - Control-Flow
---
### What is a `do while` loop?

- Executes the loop body **at least once**.
- Checks the condition **after** the loop body runs.
- Runs again if condition is `True`.

---

### How to simulate in Python?

Use a `while True` loop with a `break` inside based on the condition at the **end** of the loop.

```Python
while True:
    # loop body code here

    if not condition:
        break
```

---

### Simulated `do while` example:

```Python
count = 0

while True:
    print(count)
    count += 1

    if count >= 5:
        break
```

---

### Summary Table

|Concept|Syntax / Usage|Description|
|---|---|---|
|Simulate do while|`while True:` + `if not condition: break`|Run loop at least once, check condition after|
|Loop body|Code inside `while True:`|Executes before condition check|
|Condition check|`if not condition: break`|Break loop if condition no longer met|

---

### Real-World Example: User Input Validation

Ask the user for a positive number — keep asking **at least once** until they enter a valid number.

```Python
while True:
    num = int(input("Enter a positive number: "))
    if num > 0:
        print(f"Thanks! You entered {num}")
        break
    else:
        print("Invalid input. Try again.")
```