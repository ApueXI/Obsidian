---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. What are Built-in Functions?

- Python provides **many functions ready to use without imports** — these are **built-in functions**.
- They cover common tasks like type conversion, math, input/output, iteration, and more.

---

## 2. Common Built-in Functions (Grouped by Use)

|Category|Functions|Purpose|
|---|---|---|
|**Type Conversion**|`int()`, `float()`, `str()`, `bool()`, `list()`, `tuple()`, `set()`, `dict()`|Convert data types|
|**Math & Number**|`abs()`, `round()`, `pow()`, `divmod()`, `max()`, `min()`, `sum()`|Arithmetic and aggregates|
|**Sequence & Iterables**|`len()`, `range()`, `enumerate()`, `sorted()`, `reversed()`, `all()`, `any()`|Work with lists, tuples, iterables|
|**Object Introspection**|`type()`, `id()`, `isinstance()`, `issubclass()`, `dir()`, `help()`|Inspect objects and types|
|**Input/Output**|`print()`, `input()`|Console I/O|
|**Functional**|`map()`, `filter()`, `zip()`, `eval()`, `exec()`, `callable()`|Functional programming and dynamic code|
|**Others**|`open()`, `hash()`, `format()`, `chr()`, `ord()`, `bin()`, `oct()`, `hex()`|Various utility functions|

---

## 3. Examples of Common Built-in Functions

```Python
# Type conversion
print(int("123"))        # 123
print(float("3.14"))     # 3.14

# Math
print(abs(-7))           # 7
print(pow(2, 3))         # 8

# Sequence
print(len([1, 2, 3]))    # 3
print(sorted([3, 1, 2])) # [1, 2, 3]

# Iterables
print(list(map(str, [1, 2, 3])))       # ['1', '2', '3']
print(list(filter(lambda x: x > 1, [1, 2, 3])))  # [2, 3]

# Object inspection
print(type(42))          # <class 'int'>
print(isinstance(42, int)) # True

# Input/Output
# name = input("Enter your name: ")
# print(f"Hello, {name}!")
```

---

## 4. Summary Table

|Function|Purpose|Example|
|---|---|---|
|`int()`|Convert to integer|`int("5") -> 5`|
|`float()`|Convert to float|`float("3.14") -> 3.14`|
|`str()`|Convert to string|`str(10) -> "10"`|
|`len()`|Length of iterable|`len([1,2,3]) -> 3`|
|`print()`|Output to console|`print("Hi")`|
|`input()`|Input from user|`input("Name? ")`|
|`range()`|Generate sequence of numbers|`range(5)`|
|`map()`|Apply function to iterable|`map(str, [1,2])`|
|`filter()`|Filter iterable by function|`filter(lambda x: x>0, [-1,1])`|
|`sorted()`|Return sorted list|`sorted([3,1,2])`|
|`type()`|Get type of object|`type(10)`|
|`isinstance()`|Check type or subclass|`isinstance(10, int)`|

---

## 5. Real-World Example: Using Built-ins to Process Data

```Python
data = ["10", "25", "-3", "42"]

# Convert strings to integers, filter positives, sort, and print
numbers = list(map(int, data))
positive_numbers = list(filter(lambda x: x > 0, numbers))
sorted_numbers = sorted(positive_numbers)

print(sorted_numbers)  # Output: [10, 25, 42]
```