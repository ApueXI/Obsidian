---
Created: 2025-08-21T19:29
tags:
  - Basic-Syntax
---
## ✅ What is a Variable?

A **variable** stores data in memory with a name.

```Python
x = 10        # integer
name = "Bob"  # string
price = 19.99 # float
```

---

## ✅ Naming Rules

✔ **Must start with a letter or underscore** `**_**`

✔ Can contain **letters, numbers, underscores**

✔ **Case-sensitive** (`Age` ≠ `age`)

✔ Cannot use **Python keywords** (`if`, `for`, `class`, etc.)

✔ Should be **descriptive**

✅ **Valid:**

```Python
my_var = 1
_age = 20
userName = "Alice"
PI = 3.1416
```

❌ **Invalid:**

```Python
2name = "Bob"    # starts with number
my-var = 10      # dash not allowed
class = "oops"   # keyword
```

---

## ✅ Recommended Naming Conventions

✔ **snake_case** → preferred for variables

✔ **UPPER_CASE** → constants

✔ **CamelCase** → classes

```Python
first_name = "Alice"   # variable
MAX_LIMIT = 100        # constant
class MyClass: pass    # class
```

---

## ✅ Multiple Assignment

```Python
a, b, c = 1, 2, 3
x = y = z = 0  # same value for all
```

---

## ✅ Dynamic Typing

Python variables **don’t need explicit types**

```Python
x = 10       # int
x = "hello"  # now string
```

---

## ✅ Checking Variable Type

```Python
age = 25
print(type(age))  # <class 'int'>
```