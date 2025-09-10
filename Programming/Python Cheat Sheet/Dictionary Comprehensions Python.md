---
Created: 2025-08-21T19:29
tags:
  - Comprehensions
---
## 1. What is a Dictionary Comprehension?

- A concise way to **create dictionaries** using a single line of code.
- Similar to list comprehensions but produces **key-value pairs**.
- Syntax combines a **key: value expression** with a loop and optional conditions.

---

## 2. Basic Syntax

```Python
{key_expression: value_expression for item in iterable}
```

- Creates a new dictionary by evaluating **key_expression** and **value_expression** for each item.

---

## 3. With Conditionals (Filter)

```Python
{key: value for item in iterable if condition}
```

- Includes only items where **condition** is `True`.

---

## 4. Examples

### Create dict of numbers and their squares

```Python
squares = {x: x**2 for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

### Filter dict for even keys

```Python
filtered = {x: x**2 for x in range(5) if x % 2 == 0}
print(filtered)  # {0: 0, 2: 4, 4: 16}
```

### Create dict from list of tuples

```Python
pairs = [("a", 1), ("b", 2), ("c", 3)]
dict_comp = {k: v for k, v in pairs}
print(dict_comp)  # {'a': 1, 'b': 2, 'c': 3}
```

---

## 5. Using `if-else` in Value Expression

```Python
result = {x: ("even" if x % 2 == 0 else "odd") for x in range(5)}
print(result)  # {0: 'even', 1: 'odd', 2: 'even', 3: 'odd', 4: 'even'}
```

---

## Summary Table

|Syntax|Description|Example Output|
|---|---|---|
|`{k: v for item in iterable}`|Basic dict comprehension|`{0: 0, 1: 1, 2: 4}`|
|`{k: v for item in iterable if condition}`|Filter items|`{0: 0, 2: 4}`|
|`{k: (val_if_true if cond else val_if_false) for item}`|Conditional values|`{0: 'even', 1: 'odd'}`|

---

## Real-World Example: Word Frequency Count

```Python
sentence = "the quick brown fox jumps over the lazy dog the quick fox"
words = sentence.split()

freq = {word: words.count(word) for word in set(words)}
print(freq)
```

**Output:**

```Plain
{'brown': 1, 'lazy': 1, 'fox': 2, 'dog': 1, 'quick': 2, 'jumps': 1, 'over': 1, 'the': 3}
```

✅ Quickly counts occurrences of each unique word in a sentence.