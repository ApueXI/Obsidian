---
Created: 2025-08-21T19:29
tags:
  - Control-Flow
---
Loop control statements allow you to modify the behavior of loops (`for` or `while`) — to **exit early**, **skip iterations**, or run code conditionally.

---

### Loop Control Keywords

|Keyword|Purpose|Description|
|---|---|---|
|`break`|Exit loop immediately|Stops loop execution and moves to code after the loop|
|`continue`|Skip current iteration and proceed|Skips remaining loop body for current iteration, starts next loop cycle|
|`else`|Run block after loop completes normally|Executes if loop wasn’t terminated by `break`|

---

### Detailed Usage

### 1. `break`

- Exits loop immediately.
- Useful to stop loop once a condition is met.

```Python
for i in range(10):
    if i == 5:
        break
    print(i)
# Prints 0 1 2 3 4 and then stops
```

### 2. `continue`

- Skips rest of current iteration, goes to next.
- Useful to skip over unwanted cases.

```Python
for i in range(5):
    if i == 3:
        continue
    print(i)
# Prints 0 1 2 4 (skips 3)
```

### 3. `else` after loop

- Executes if loop ends normally (no `break`).
- Useful for searching patterns, to confirm loop ran completely.

```Python
for i in range(3):
    print(i)
else:
    print("Loop completed without break")
```

- In contrast:

```Python
for i in range(3):
    if i == 1:
        break
else:
    print("This will NOT print because loop was broken")
```

---

### Summary Table

|Statement|Usage|Effect|When to Use|
|---|---|---|---|
|`break`|`break`|Exit loop immediately|Stop loop on condition|
|`continue`|`continue`|Skip to next loop iteration|Skip processing certain cases|
|`else` on loops|`for/while... else:`|Run block if loop finished normally|Confirm loop completion without breaks|

---

### Real-World Example: Searching a List

Find if a number exists in a list and act accordingly.

```Python
numbers = [3, 7, 10, 15, 20]
target = 10

for num in numbers:
    if num == target:
        print(f"{target} found!")
        break
else:
    print(f"{target} not found in the list.")
```