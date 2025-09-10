---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `len()`

- Returns the **number of items** in an object (like list, string, tuple, dictionary, set, etc.)

### Syntax:

```Python
len(obj)
```

### Examples:

```Python
len([1, 2, 3])       # 3
len("hello")         # 5
len({"a": 1, "b": 2}) # 2
```

---

## 2. `sum()`

- Returns the **sum of all items** in an iterable (usually numbers).
- Can take an optional **start** value (default is 0).

### Syntax:

```Python
sum(iterable, start=0)
```

### Examples:

```Python
sum([1, 2, 3])        # 6
sum([1, 2, 3], 10)    # 16 (starts from 10)
```

---

## 3. `max()`

- Returns the **maximum item** from an iterable or two or more arguments.

### Syntax:

```Python
max(iterable, *[, key, default])
max(arg1, arg2, *args[, key])
```

### Examples:

```Python
max([1, 5, 3])          # 5
max(1, 5, 3)            # 5
max("banana")           # 'n' (max character in alphabetical order)

# Using key function
max(["apple", "banana", "cherry"], key=len)  # 'banana'
```

---

## 4. `min()`

- Returns the **minimum item** from an iterable or two or more arguments.

### Syntax:

```Python
min(iterable, *[, key, default])
min(arg1, arg2, *args[, key])
```

### Examples:

```Python
min([1, 5, 3])          # 1
min(1, 5, 3)            # 1
min("banana")           # 'a' (min character in alphabetical order)

# Using key function
min(["apple", "banana", "cherry"], key=len)  # 'apple'
```

---

## Summary Table

|Function|Purpose|Basic Syntax|Example|
|---|---|---|---|
|`len()`|Number of items in an object|`len(obj)`|`len([1, 2, 3]) -> 3`|
|`sum()`|Sum of all elements|`sum(iterable, start=0)`|`sum([1, 2, 3]) -> 6`|
|`max()`|Maximum element|`max(iterable)`|`max([1, 5, 3]) -> 5`|
|`min()`|Minimum element|`min(iterable)`|`min([1, 5, 3]) -> 1`|

---

## Real-World Example: Analyzing Scores

```Python
scores = [88, 92, 79, 93, 85]

print("Number of scores:", len(scores))           # 5
print("Total score:", sum(scores))                 # 437
print("Highest score:", max(scores))               # 93
print("Lowest score:", min(scores))                # 79
```

---

Want me to cover **other related built-ins like** `**all()**`**,** `**any()**`**, or how to use these with generators?**