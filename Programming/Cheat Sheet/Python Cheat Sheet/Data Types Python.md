---
Created: 2025-08-21T19:29
tags:
  - Basic-Syntax
---
## ✅ Built-in Data Types

### 🔢 **Numeric Types**

- **int** → whole numbers
- **float** → decimal numbers
- **complex** → complex numbers

```Python
x = 10        # int
y = 3.14      # float
z = 2 + 3j    # complex
```

---

### 🔤 **Text Type**

- **str** → string of characters

```Python
name = "Alice"
```

---

### ✅ **Sequence Types**

- **list** → ordered, mutable
- **tuple** → ordered, immutable
- **range** → sequence of numbers

```Python
fruits = ["apple", "banana", "cherry"]  # list
coords = (10, 20)                      # tuple
numbers = range(5)                     # 0,1,2,3,4
```

---

### ✅ **Mapping Type**

- **dict** → key-value pairs

```Python
person = {"name": "Alice", "age": 25}
```

---

### ✅ **Set Types**

- **set** → unordered, unique elements
- **frozenset** → immutable set

```Python
unique_nums = {1, 2, 3, 3}  # {1,2,3}
```

---

### ✅ **Boolean Type**

- **bool** → `True` or `False`

```Python
is_active = True
```

---

### ✅ **Binary Types**

- **bytes**, **bytearray**, **memoryview**

```Python
b = b"Hello"             # bytes
ba = bytearray(5)        # mutable bytes
```

---

### ✅ **None Type**

- **None** → represents no value

```Python
x = None
```

---

## ✅ Type Checking & Conversion

```Python
x = 42
print(type(x))       # <class 'int'>
print(str(42))       # "42"
print(int("123"))    # 123
print(float(5))      # 5.0
```

---

## ✅ Type Categories

- **Mutable:** list, dict, set, bytearray
- **Immutable:** int, float, str, tuple, frozenset, bytes