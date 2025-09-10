---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `type()`

- Returns the **exact type (class)** of an object.
- **Does NOT check inheritance**—only the immediate type.

### Syntax:

```Python
type(obj)
```

### Examples:

```Python
print(type(42))          # <class 'int'>
print(type("hello"))     # <class 'str'>
print(type([1, 2]))      # <class 'list'>

# Checking exact type
x = 42
if type(x) is int:
    print("x is exactly an int")
```

---

## 2. `isinstance()`

- Checks if an object is an **instance of a class or any subclass**.
- **Considers inheritance**, unlike `type()`.

### Syntax:

```Python
isinstance(obj, class_or_tuple)
```

### Examples:

```Python
print(isinstance(42, int))               # True
print(isinstance(3.14, (int, float)))    # True (matches float)
print(isinstance("hi", list))            # False

# Inheritance case
class Animal: pass
class Dog(Animal): pass

d = Dog()
print(isinstance(d, Dog))      # True
print(isinstance(d, Animal))   # True (because Dog inherits Animal)
print(type(d) is Animal)       # False (exact type is Dog)
```

---

## Key Difference

|Feature|`type(obj)`|`isinstance(obj, Class)`|
|---|---|---|
|Checks|Exact class only|Class **or any subclass**|
|Inheritance|❌ Does **NOT** consider|✅ **Considers inheritance**|
|Usage|Strict type matching|More flexible type checking|
|Example|`type(d) is Dog` → True|`isinstance(d, Animal)` → True|

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`type(obj)`|Get exact class of object|`type(42)` → `<class 'int'>`|
|`isinstance()`|Check if object is instance/subclass|`isinstance(d, Animal)` → True|

---

## Real-World Examples

### ✅ Strict Type Matching with `type()`

```Python
value = [1, 2, 3]

if type(value) is list:
    print("Value is a list!")
```

---

### ✅ Flexible Type Checking with `isinstance()`

```Python
def process_number(x):
    if isinstance(x, (int, float)):
        print("Valid number:", x)
    else:
        print("Not a number!")

process_number(10)       # Valid number
process_number(3.14)     # Valid number
process_number("hi")     # Not a number!
```

---

### ✅ Inheritance Check

```Python
class Shape: pass
class Circle(Shape): pass

c = Circle()
print(type(c) is Shape)       # False
print(isinstance(c, Shape))  # True
```

---

## TL;DR

- **Use** `**type()**` when you need **exact type** (no inheritance).
- **Use** `**isinstance()**` when you want to allow **subclasses** too.