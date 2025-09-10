---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `print()`

- Prints objects to the console (stdout).
- Supports **multiple arguments**, custom separator `sep`, and end character `end`.

### Syntax:

```Python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

### Examples:

```Python
print("Hello", "World")            # Hello World
print("A", "B", sep="-")           # A-B
print("No newline", end="")        # No newline (no \n)
print("Next line")                 # Next line
```

---

## 2. `input()`

- Reads a **string from user input** (stdin).
- Always returns a **string**, so you need type conversion for numbers.

### Syntax:

```Python
input(prompt='')
```

### Examples:

```Python
name = input("Enter your name: ")
print("Hello,", name)

age = int(input("Enter your age: "))  # convert to int
print("In 5 years you’ll be", age + 5)
```

---

## 3. `open()`

- Opens a **file** and returns a **file object**.
- Used for reading, writing, or appending.

### Syntax:

```Python
open(file, mode='r', encoding=None)
```

### Common modes:

- `'r'` → read
- `'w'` → write (overwrites)
- `'a'` → append
- `'b'` → binary mode (e.g., `'rb'`)
- `'+'` → read & write

### Example:

```Python
# Writing to a file
with open("example.txt", "w") as f:
    f.write("Hello, File!")

# Reading from a file
with open("example.txt", "r") as f:
    content = f.read()
    print(content)  # Hello, File!
```

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`print()`|Output to console|`print("Hello", sep="-")` → `Hello`|
|`input()`|Get user input (string)|`name = input("Name? ")`|
|`open()`|Open a file for read/write operations|`with open("f.txt", "r") as f:`|

---

## Real-World Example: Saving User Data

```Python
# Take user input
name = input("Enter your name: ")
age = int(input("Enter your age: "))

# Print confirmation
print(f"Saving {name} (age {age})...")

# Save to file
with open("users.txt", "a") as f:
    f.write(f"{name},{age}\n")

# Read back file
print("\nCurrent users:")
with open("users.txt", "r") as f:
    print(f.read())
```