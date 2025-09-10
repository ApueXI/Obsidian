---
Created: 2025-08-21T19:29
tags:
  - Comprehensions
---
  

## 1. What is a List Comprehension?

- A concise way to **create lists** using a single line of code.
- Combines a **for loop** and **optional conditionals** inside square brackets.
- More readable and often faster than traditional loops.

---

## 2. Basic Syntax

```Python
[expression for item in iterable]
```

- Creates a new list by evaluating the **expression** for each **item**.

---

## 3. With Conditionals (Filter)

```Python
[expression for item in iterable if condition]
```

- Includes only items where **condition** is `True`.

---

## 4. Examples

### Create list of squares

```Python
squares = [x**2 for x in range(5)]
print(squares)  # [0, 1, 4, 9, 16]
```

### Filter even numbers

```Python
evens = [x for x in range(10) if x % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8]
```

### Convert strings to uppercase

```Python
words = ["apple", "banana", "cherry"]
upper_words = [w.upper() for w in words]
print(upper_words)  # ['APPLE', 'BANANA', 'CHERRY']
```

---

## 5. Nested Loops in Comprehensions

```Python
pairs = [(x, y) for x in [1, 2] for y in [3, 4]]
print(pairs)  # [(1, 3), (1, 4), (2, 3), (2, 4)]
```

---

## 6. Using `if-else` in Expression

```Python
result = [x if x % 2 == 0 else -x for x in range(5)]
print(result)  # [0, -1, 2, -3, 4]
```

---

## Summary Table

|Syntax|Description|Example Output|
|---|---|---|
|`[expr for item in iterable]`|Basic comprehension|`[0,1,4,9]`|
|`[expr for item in iterable if cond]`|Filter items|`[0,2,4,6]`|
|`[expr1 if cond else expr2 for item in iterable]`|Conditional expression|`[0,-1,2,-3]`|
|Nested loops|Multiple for loops|`[(1,3),(1,4),(2,3),(2,4)]`|

---

## Real-World Example: Filter & Transform Usernames

```Python
usernames = ["alice", "Bob123", "carol!", "dave42"]

cleaned = [u.lower() for u in usernames if u.isalpha()]
print(cleaned)
```

**Output:**

```Plain
['alice']
```

✅ Filters out usernames with digits or punctuation, converts to lowercase