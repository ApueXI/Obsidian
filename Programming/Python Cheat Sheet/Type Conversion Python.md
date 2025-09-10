---
Created: 2025-08-21T19:29
tags:
  - Basic-Syntax
---
## ✅ What is Type Conversion?

Changing a value from one **data type** to another.

- **Implicit conversion** → done automatically by Python
- **Explicit conversion** → manually using casting functions

---

## ✅ 1. Implicit Type Conversion

Python automatically converts **smaller → larger** type when needed.

```Python
x = 5       # int
y = 2.5     # float
result = x + y
print(result)      # 7.5 (float)
print(type(result)) # <class 'float'>
```

---

## ✅ 2. Explicit Type Conversion (Type Casting)

### 🔢 **Numbers**

```Python
int("10")        # 10
float("3.14")    # 3.14
complex(5)       # (5+0j)
```

---

### 🔤 **Strings**

```Python
str(123)        # "123"
str(3.14)       # "3.14"
```

---

### ✅ **Boolean**

```Python
bool(0)         # False
bool("")        # False
bool("Hi")      # True
bool(123)       # True
```

---

### ✅ **Collections**

```Python
list("abc")        # ['a', 'b', 'c']
tuple([1,2,3])     # (1,2,3)
set([1,2,2,3])     # {1,2,3}
dict([("a",1),("b",2)])  # {'a':1,'b':2}
```

---

### ✅ **ASCII & Unicode**

```Python
ord('A')   # 65 (char → ASCII)
chr(65)    # 'A' (ASCII → char)
```

---

## ✅ Common Gotchas

❌ `int("3.14")` → **error** (must be whole number string)

✅ `int(float("3.14"))` → 3

---

## ✅ Quick Reference Table

|Convert To|Function|
|---|---|
|Integer|`int(x)`|
|Float|`float(x)`|
|String|`str(x)`|
|Boolean|`bool(x)`|
|List|`list(x)`|
|Tuple|`tuple(x)`|
|Set|`set(x)`|
|Dict|`dict(x)`|
|Complex|`complex(x)`|