---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `dir()`

- Returns a **list of valid attributes and methods** of an object.
- If called **without arguments**, it shows **names in the current local scope**.

---

### Syntax

```Python
dir([object])
```

- `dir()` → names in current scope
- `dir(object)` → attributes/methods of that object

---

### Examples

```Python
# Attributes/methods of a list
print(dir([]))
# ['__add__', '__class__', ..., 'append', 'clear', 'copy', 'count', 'extend', ...]

# Current local scope
x = 42
def func(): pass
print(dir())
# ['__annotations__', '__builtins__', ..., 'func', 'x']
```

---

## 2. `help()`

- Launches the **built-in help system** or shows the **docstring** for an object.
- Displays detailed info, including docstrings, available methods, and usage.

---

### Syntax

```Python
help(object)
```

---

### Examples

```Python
help(list)        # Shows documentation for the list class
help(str.upper)   # Shows documentation for the upper() method of str

# Interactive help mode
# help()  # then type a topic like 'str'
```

---

## Key Differences

|Feature|`dir()`|`help()`|
|---|---|---|
|**What it does**|Lists available attributes/methods|Shows documentation & explanations|
|**Returns**|A list of strings|Prints text (no return value)|
|**Use case**|Quick lookup of names|Detailed help / docstring reference|
|**Example**|`dir([])` → list methods|`help(list)` → explains list methods|

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`dir()`|List names in scope or object methods|`dir("hi")` → `['__add__','upper',...]`|
|`help()`|Show docstring/help for object|`help(str.upper)` → prints usage info|

---

## Real-World Examples

### ✅ Exploring an Unknown Object

```Python
value = {"a": 1, "b": 2}

print("What can we do with a dict?")
print(dir(value))    # shows all methods

help(value.get)      # shows how get() works
```

---

### ✅ Debugging in Interactive Mode

```Python
nums = [1, 2, 3]
print(dir(nums))     # See all list methods
help(nums.append)    # See what append() does
```

---

### ✅ Discovering Built-in Functions

```Python
# See all built-in names
print(dir(__builtins__))

# Learn about a specific one
help(abs)
```

---

## TL;DR

- **Use** `**dir()**` → to **see what’s available**.
- **Use** `**help()**` → to **learn how it works**.