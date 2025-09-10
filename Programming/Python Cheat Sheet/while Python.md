---
Created: 2025-08-21T19:29
tags:
  - Control-Flow
---
### Basic Syntax

```Python
while condition:
    # code block
```

- Runs repeatedly **as long as** `condition` is `True`.
- Condition is checked **before** each iteration.
- Can potentially run forever if condition never becomes False (infinite loop).

---

### Detailed Info and Variations

- Basic `while` loop example:

```Python
count = 0
while count < 5:
    print(count)
    count += 1
```

- Using `break` to exit loop early:

```Python
while True:
    user_input = input("Enter 'exit' to stop: ")
    if user_input == 'exit':
        break
    print(f"You typed: {user_input}")
```

- Using `continue` to skip rest of the loop iteration:

```Python
i = 0
while i < 5:
    i += 1
    if i == 3:
        continue  # skip printing 3
    print(i)
```

- Using `else` block with `while` loop — runs if loop finishes normally (no `break`):

```Python
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("Loop finished without break")
```

- Nested while loops:

```Python
i = 0
while i < 3:
    j = 0
    while j < 2:
        print(i, j)
        j += 1
    i += 1
```

- Infinite loop example (usually avoid unless intentional):

```Python
while True:
    print("This will print forever unless break is called")
    break  # Make sure to include break somewhere to avoid infinite loop
```

---

### Summary Table

|Concept|Syntax / Usage|Description|
|---|---|---|
|Basic loop|`while condition:`|Loop while condition is True|
|Break loop|`break`|Exit loop immediately|
|Skip iteration|`continue`|Skip rest of current iteration|
|Loop else|`while... else:`|Run block if loop exits normally (no break)|
|Nested while loops|`while...: while...:`|Loop inside another loop|
|Infinite loop|`while True:`|Loop runs forever unless broken|

---

### Real-World Example: Password Prompt

A program keeps asking for a password until the user enters the correct one.

```Python
correct_password = "open123"
attempts = 0

while attempts < 3:
    pwd = input("Enter password: ")
    if pwd == correct_password:
        print("Access granted")
        break
    else:
        print("Wrong password")
        attempts += 1
else:
    print("Too many failed attempts. Access denied.")
```