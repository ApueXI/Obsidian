---
Created: 2025-08-21T19:29
tags:
  - Comprehensions
---
## 1. What is a Generator Expression?

- A **compact way to create generators** using a syntax similar to list comprehensions but with parentheses `()`.
- Generates items **lazily**, one at a time, saving memory.
- Useful for **large data** or infinite sequences.

---

## 2. Basic Syntax

```Python
(expression for item in iterable)
```

- Creates a **generator object** that produces values on-demand.

---

## 3. With Conditionals (Filter)

```Python
(expression for item in iterable if condition)
```

- Yields only items where **condition** is `True`.

---

## 4. Examples

### Generator for squares

```Python
gen = (x**2 for x in range(5))
print(gen)         # <generator object ...>

for val in gen:
    print(val)
# Output: 0 1 4 9 16 (each on a new line)
```

### Sum of squares (memory efficient)

```Python
total = sum(x**2 for x in range(1000000))  # Doesn't create a full list in memory
print(total)
```

---

## 5. Using `next()` with Generators

```Python
gen = (x**2 for x in range(3))
print(next(gen))  # 0
print(next(gen))  # 1
print(next(gen))  # 4
# next(gen) now raises StopIteration
```

---

## 6. Why Use Generator Expressions?

- **Memory efficient** — generate items as needed, not all at once.
- Useful for **stream processing**, **large datasets**, or **pipelines**.
- Can be passed to functions like `sum()`, `any()`, `all()`, `list()`, etc.

---

## Summary Table

|Feature|Example|Description|
|---|---|---|
|Basic generator expression|`(x**2 for x in range(5))`|Create a generator object|
|With condition|`(x for x in range(10) if x % 2 == 0)`|Filtered generator|
|Iterate generator|`for val in gen:`|Iterate values lazily|
|Get next item|`next(gen)`|Get next value|

---

## Real-World Example: Reading Large File Lines

Suppose you want to process a big file line by line without loading it all into memory:

```Python
def read_large_file(file_path):
    with open(file_path, 'r') as f:
        # Generator expression to strip each line lazily
        lines = (line.strip() for line in f)
        for line in lines:
            if line:  # Skip empty lines
                print(line)

# Usage (assuming 'bigfile.txt' exists)
# read_large_file('bigfile.txt')
```

✅ Efficient line-by-line processing without loading entire file into memory.