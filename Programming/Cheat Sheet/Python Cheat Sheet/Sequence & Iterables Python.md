---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `len()`

- Returns the **number of items** in an object (string, list, tuple, dict, etc.).

### Syntax:

```Python
len(obj)
```

### Examples:

```Python
len("hello")       # 5
len([1, 2, 3, 4])  # 4
len({"a": 1})      # 1
```

---

## 2. `range()`

- Returns an **immutable sequence of numbers** (often used in loops).
- Default start = 0, default step = 1.

### Syntax:

```Python
range(stop)
range(start, stop[, step])
```

### Examples:

```Python
list(range(5))        # [0, 1, 2, 3, 4]
list(range(2, 7))     # [2, 3, 4, 5, 6]
list(range(10, 0, -2))# [10, 8, 6, 4, 2]
```

---

## 3. `enumerate()`

- Adds an **index counter** to an iterable, returning `(index, value)` pairs.
- Useful for looping with both index & value.

### Syntax:

```Python
enumerate(iterable, start=0)
```

### Examples:

```Python
for i, val in enumerate(["a", "b", "c"], start=1):
    print(i, val)
# 1 a
# 2 b
# 3 c
```

---

## 4. `sorted()`

- Returns a **new sorted list** from an iterable (does NOT modify original).
- Optional `key` for custom sorting, and `reverse=True` for descending.

### Syntax:

```Python
sorted(iterable, key=None, reverse=False)
```

### Examples:

```Python
sorted([3, 1, 2])                       # [1, 2, 3]
sorted(["apple", "pear"], key=len)      # ['pear', 'apple']
sorted([3, 1, 2], reverse=True)         # [3, 2, 1]
```

---

## 5. `reversed()`

- Returns an **iterator** that accesses the given sequence in reverse order.

### Syntax:

```Python
reversed(sequence)
```

### Examples:

```Python
list(reversed([1, 2, 3]))  # [3, 2, 1]
"".join(reversed("abc"))   # "cba"
```

---

## 6. `all()`

- Returns **True if ALL elements** of an iterable are truthy (or if iterable is empty).

### Syntax:

```Python
all(iterable)
```

### Examples:

```Python
all([True, True, 1])    # True
all([True, False, 1])   # False
all([])                # True (empty is considered True)
```

---

## 7. `any()`

- Returns **True if ANY element** of an iterable is truthy.
- Returns **False only if all elements are falsy or iterable is empty**.

### Syntax:

```Python
any(iterable)
```

### Examples:

```Python
any([0, False, 5])   # True
any([0, "", None])   # False
any([])              # False
```

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`len()`|Count items in iterable|`len("abc") -> 3`|
|`range()`|Generate number sequence|`list(range(3)) -> [0,1,2]`|
|`enumerate()`|Get index-value pairs|`enumerate(['a','b'])`|
|`sorted()`|Return sorted list|`sorted([3,1,2]) -> [1,2,3]`|
|`reversed()`|Reverse sequence (returns iterator)|`list(reversed([1,2])) -> [2,1]`|
|`all()`|True if all elements truthy|`all([1,2,3]) -> True`|
|`any()`|True if any element truthy|`any([0,0,1]) -> True`|

---

## Real-World Example: Checking Student Scores

```Python
scores = [85, 90, 78, 92]

print("Number of students:", len(scores))           # 4
print("Scores sorted:", sorted(scores))             # [78, 85, 90, 92]
print("Scores reversed:", list(reversed(scores)))   # [92, 78, 90, 85]

# Check if all students passed (>= 50)
print("All passed:", all(score >= 50 for score in scores))  # True

# Check if anyone got a perfect score
print("Any perfect score:", any(score == 100 for score in scores))  # False

# Print with indexes
for idx, score in enumerate(scores, start=1):
    print(f"Student {idx}: {score}")
```