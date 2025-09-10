---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## What is `enumerate()`?

- Adds an **automatic counter (index)** to an iterable.
- Returns an **enumerate object** → which yields **(index, value)** pairs.
- Useful when you need **both index & value** in a loop.

---

## Syntax

```Python
enumerate(iterable, start=0)
```

- **iterable** → list, tuple, string, etc.
- **start** → the starting index (default = 0).

---

## Basic Examples

```Python
letters = ['a', 'b', 'c']

for index, letter in enumerate(letters):
    print(index, letter)
# 0 a
# 1 b
# 2 c

# Custom start index
for index, letter in enumerate(letters, start=1):
    print(index, letter)
# 1 a
# 2 b
# 3 c

# Convert to list of tuples
print(list(enumerate(letters)))
# [(0, 'a'), (1, 'b'), (2, 'c')]
```

---

## When to Use

✅ Instead of `range(len(...))`

```Python
# ❌ Old way
for i in range(len(letters)):
    print(i, letters[i])

# ✅ Better way
for i, letter in enumerate(letters):
    print(i, letter)
```

---

## Summary Table

|Feature|Description|Example|
|---|---|---|
|**Purpose**|Add index to iterable items|`enumerate(['x','y'])` → `[(0,'x'),(1,'y')]`|
|**Returns**|`enumerate` object (iterator)|`list(enumerate('hi'))` → `[(0,'h'),(1,'i')]`|
|**Start arg**|Start index (default `0`)|`enumerate(['a'], start=5)` → `[(5,'a')]`|

---

## Real-World Examples

### ✅ Processing Student Scores with Index

```Python
students = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 78]

for i, (name, score) in enumerate(zip(students, scores), start=1):
    print(f"{i}. {name} scored {score}")
# 1. Alice scored 85
# 2. Bob scored 90
# 3. Charlie scored 78
```

---

### ✅ Highlighting Search Results

```Python
words = ["apple", "banana", "cherry", "date"]
search = "cherry"

for i, word in enumerate(words):
    if word == search:
        print(f"Found '{search}' at index {i}")
```

---

### ✅ Creating Indexed Dictionary

```Python
fruits = ["apple", "banana", "cherry"]
indexed_fruits = dict(enumerate(fruits))
print(indexed_fruits)
# {0: 'apple', 1: 'banana', 2: 'cherry'}
```

---

## Key Points

- `enumerate()` is **memory-efficient** (lazy iterator).
- Saves you from manually tracking indexes.
- Works well with `zip()` and `list()` when you need more contro