---
Created: 2025-08-21T19:29
tags:
  - Function
---
## 1. What is a Lambda Function?

- A **small anonymous function** defined with the `lambda` keyword.
- Can have **any number of arguments** but only **one expression**.
- Commonly used for **short, simple functions**.

---

## 2. Syntax

```Python
lambda arguments: expression
```

- The expression is **automatically returned**.
- No need for `return` keyword.

---

## 3. Basic Examples

```Python
square = lambda x: x ** 2
print(square(5))  # 25
```

```Python
add = lambda a, b: a + b
print(add(3, 4))  # 7
```

✅ Works like a normal function but shorter.

---

## 4. When to Use Lambda

- As a **short, throwaway function** (instead of defining with `def`).
- Often used with **functions like** `**map()**`**,** `**filter()**`**,** `**sorted()**`**, and** `**reduce()**`.

---

## 5. Lambda with Built-in Functions

### `map()` – Apply function to each item

```Python
nums = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, nums))
print(squared)  # [1, 4, 9, 16]
```

---

### `filter()` – Keep items that match condition

```Python
nums = [1, 2, 3, 4, 5, 6]
even = list(filter(lambda x: x % 2 == 0, nums))
print(even)  # [2, 4, 6]
```

---

### `sorted()` – Custom sort key

```Python
words = ["apple", "banana", "kiwi"]
sorted_words = sorted(words, key=lambda w: len(w))
print(sorted_words)  # ['kiwi', 'apple', 'banana']
```

---

### `reduce()` – Cumulative reduction

```Python
from functools import reduce

nums = [1, 2, 3, 4]
product = reduce(lambda x, y: x * y, nums)
print(product)  # 24
```

---

## 6. Lambda vs def

✅ **Lambda** → single-expression, inline, anonymous

✅ **def** → multi-line, reusable, named

```Python
# Lambda
double = lambda x: x * 2

# Equivalent with def
def double_func(x):
    return x * 2
```

---

## Summary Table

|Feature|Example|Description|
|---|---|---|
|Basic lambda|`lambda x: x + 1`|One-line function|
|Multiple args|`lambda a, b: a * b`|Can accept multiple arguments|
|With map()|`map(lambda x: x**2, nums)`|Transform elements|
|With filter()|`filter(lambda x: x>0, nums)`|Filter elements|
|With sorted()|`sorted(list, key=lambda x: ...)`|Custom sort|
|With reduce()|`reduce(lambda x,y:x+y, nums)`|Accumulate result|

---

## Real-World Example: Sorting Complex Data

Suppose you have a list of people (name, age) and want to sort by age.

```Python
people = [
    ("Alice", 30),
    ("Bob", 25),
    ("Charlie", 35)
]

# Sort by age
sorted_people = sorted(people, key=lambda person: person[1])
print(sorted_people)
```

**Output:**

```Plain
[('Bob', 25), ('Alice', 30), ('Charlie', 35)]
```

✅ Quick sorting without defining a full function