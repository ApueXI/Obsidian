---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## What is `zip()`?

- **Combines multiple iterables** (lists, tuples, etc.) into an iterator of **tuples**.
- **Stops at the shortest iterable** (unless using `itertools.zip_longest`).
- Returns a **zip object** (lazy iterator).

---

## Syntax

```Python
zip(iter1, iter2, ...)
```

---

## Basic Examples

```Python
names = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 78]

zipped = zip(names, scores)
print(list(zipped))
# [('Alice', 85), ('Bob', 90), ('Charlie', 78)]
```

---

## When Iterables Have Different Lengths

```Python
a = [1, 2, 3]
b = ['x', 'y']

print(list(zip(a, b)))
# [(1, 'x'), (2, 'y')]  ← stops at shortest
```

---

## Unzipping

You can **unzip** with the `*` operator:

```Python
pairs = [(1, 'a'), (2, 'b'), (3, 'c')]
nums, letters = zip(*pairs)
print(nums)     # (1, 2, 3)
print(letters)  # ('a', 'b', 'c')
```

---

## Useful with `dict()`

```Python
keys = ["name", "age", "city"]
values = ["Alice", 25, "NY"]

person = dict(zip(keys, values))
print(person)
# {'name': 'Alice', 'age': 25, 'city': 'NY'}
```

---

## Summary Table

|Feature|Description|Example|
|---|---|---|
|**Purpose**|Combine iterables into tuples|`zip([1,2],['a','b']) → [(1,'a'),(2,'b')]`|
|**Stops at**|Shortest iterable|`zip([1,2],[3]) → [(1,3)]`|
|**Unzipping**|Use `zip(*zipped)` to unpack|`nums, letters = zip(*pairs)`|
|**Use Case**|Pairing data, dict creation|`dict(zip(keys, values))`|

---

## Real-World Examples

### ✅ Pair Students & Scores

```Python
students = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 78]

for name, score in zip(students, scores):
    print(f"{name} scored {score}")
# Alice scored 85
# Bob scored 90
# Charlie scored 78
```

---

### ✅ Combine Multiple Lists

```Python
names = ["Alice", "Bob"]
ages = [25, 30]
cities = ["NY", "LA"]

for name, age, city in zip(names, ages, cities):
    print(f"{name} ({age}) from {city}")
```

---

### ✅ Matrix Transpose

```Python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

transposed = list(zip(*matrix))
print(transposed)
# [(1, 4), (2, 5), (3, 6)]
```

---

## Key Points

- `zip()` is **lazy** → convert with `list()` to see results.
- Stops at the **shortest iterable**.
- Can be reversed with `zip(*zipped_data)`.
- Great for pairing related data into tuples.