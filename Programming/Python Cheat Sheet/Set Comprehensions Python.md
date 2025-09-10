---
Created: 2025-08-21T19:29
tags:
  - Comprehensions
---
## 1. What is a Set Comprehension?

- A concise way to **create sets** using a single line of code.
- Similar to list and dictionary comprehensions but produces a **set** with **unique elements**.
- Syntax uses curly braces `{}` with an expression and a loop.

---

## 2. Basic Syntax

```Python
{expression for item in iterable}

```

- Creates a new set by evaluating the **expression** for each **item**.

---

## 3. With Conditionals (Filter)

```Python
{expression for item in iterable if condition}
```

- Includes only items where **condition** is `True`.

---

## 4. Examples

### Create set of squares

```Python
squares = {x**2 for x in range(5)}
print(squares)  # {0, 1, 4, 9, 16}
```

### Filter even numbers

```Python
evens = {x for x in range(10) if x % 2 == 0}
print(evens)  # {0, 2, 4, 6, 8}
```

### Remove duplicates from list

```Python
nums = [1, 2, 2, 3, 4, 4, 5]
unique_nums = {x for x in nums}
print(unique_nums)  # {1, 2, 3, 4, 5}
```

---

## Summary Table

|Syntax|Description|Example Output|
|---|---|---|
|`{expr for item in iterable}`|Basic set comprehension|`{0, 1, 4, 9}`|
|`{expr for item in iterable if cond}`|Filter items|`{0, 2, 4, 6}`|

---

## Real-World Example: Unique First Letters

Suppose you want the unique first letters of a list of words:

```Python
words = ["apple", "banana", "cherry", "avocado", "blueberry"]
first_letters = {w[0] for w in words}
print(first_letters)
```

**Output:**

```Plain
{'a', 'b', 'c'}
```

✅ Quickly extracts unique initial letters from words.