---
Created: 2025-08-21T19:29
tags:
  - Basic-Syntax
---
## ✅ Basic Usage

```Python
print("Hello, World!")
```

- Outputs text, variables, or both.

---

## ✅ Printing Variables

```Python
name = "Alice"
age = 25
print(name, age)         # Alice 25
print(f"{name} is {age}") # Alice is 25 (f-string)
print("{} is {}".format(name, age)) # Alice is 25
```

---

## ✅ Separator & End

```Python
print("A", "B", "C", sep="-")  # A-B-C
print("Hello", end=" ")        # No newline
print("World!")                # Hello World!
```

- `sep` → custom separator between items
- `end` → what to print at the end (default is `"\n"`)

---

## ✅ Printing Multiple Lines

```Python
print("Line1\nLine2\nLine3")
```

---

## ✅ Printing Without Newline

```Python
print("Hello", end="")
print("World")  # HelloWorld
```

---

## ✅ Pretty Printing

```Python
import pprint
data = {"name": "Alice", "age": 25, "skills": ["Python", "AI"]}
pprint.pprint(data)  # Nicely formatted output
```

---

## ✅ Debug Printing

```Python
x = 42
print(f"{x=}")  # x=42 (Python 3.8+)
```

---

## ✅ Printing to a File

```Python
with open("output.txt", "w") as f:
    print("Hello File!", file=f)
```