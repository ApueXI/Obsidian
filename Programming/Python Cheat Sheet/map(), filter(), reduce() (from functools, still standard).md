---
Created: 2025-08-21T19:29
tags:
  - Functional-Programming-Features
---
## 1. `map(function, iterable)`

- **Applies a function to each item** of an iterable
- Returns a **map object (iterator)** → often converted to `list()`

```Python
numbers = [1, 2, 3, 4]

# Square each number
result = map(lambda x: x**2, numbers)
print(list(result))  # [1, 4, 9, 16]
```

✅ **Use when:** you want to **transform** all elements

---

## 2. `filter(function, iterable)`

- **Filters elements** for which the function returns **True**
- Returns a **filter object (iterator)** → often converted to `list()`

```Python
numbers = [1, 2, 3, 4, 5]

# Keep even numbers
result = filter(lambda x: x % 2 == 0, numbers)
print(list(result))  # [2, 4]
```

✅ **Use when:** you want to **select only some elements**

---

## 3. `reduce(function, iterable)`

- **Reduces** an iterable to a single value by applying a function **cumulatively**
- Must be imported from `functools`

```Python
from functools import reduce

numbers = [1, 2, 3, 4]

# Sum all numbers
result = reduce(lambda x, y: x + y, numbers)
print(result)  # 10
```

✅ **Use when:** you want to **combine elements into one** (sum, product, etc.)

---

## 4. With Built-in Functions

Instead of `lambda`, you can use built-ins:

```Python
# Using map() with str.upper
words = ["hello", "world"]
print(list(map(str.upper, words)))  # ['HELLO', 'WORLD']

# Using filter() with None to remove falsy values
values = [0, 1, "", "Hi", None, True]
print(list(filter(None, values)))  # [1, 'Hi', True]
```

---

## 5. With Multiple Iterables in `map()`

```Python
a = [1, 2, 3]
b = [10, 20, 30]

# Add corresponding elements
print(list(map(lambda x, y: x + y, a, b)))  # [11, 22, 33]
```

---

## Summary Table

|Function|Purpose|Returns|
|---|---|---|
|`map(f, iterable)`|Apply function to all elements|`map` object (iterator)|
|`filter(f, iterable)`|Keep only elements where `f(x)` is True|`filter` object (iterator)|
|`reduce(f, iterable)`|Combine elements into one value cumulatively|Single value|

---

## Real-World Examples

---

### ✅ Convert Prices from USD → PHP

```Python
prices_usd = [10, 20, 30]
usd_to_php = 58.5

prices_php = map(lambda p: p * usd_to_php, prices_usd)
print(list(prices_php))  # [585.0, 1170.0, 1755.0]
```

---

### ✅ Filter Out Invalid Emails

```Python
emails = ["test@", "valid@email.com", "", "hello@site.com"]

valid_emails = filter(lambda e: "@" in e and "." in e, emails)
print(list(valid_emails))  # ['valid@email.com', 'hello@site.com']
```

---

### ✅ Sum of Squares

```Python
from functools import reduce

nums = [1, 2, 3, 4]

sum_squares = reduce(lambda acc, x: acc + x**2, nums)
print(sum_squares)  # 30
```

---

### ✅ Combine: Filter + Map + Reduce

```Python
from functools import reduce

nums = [1, 2, 3, 4, 5, 6]

result = reduce(
    lambda acc, x: acc + x,
    map(lambda x: x**2, filter(lambda x: x % 2 == 0, nums))
)
print(result)  # 56 (2² + 4² + 6²)
```

---

## TL;DR

- ✅ `**map()**` → **transform** each item
- ✅ `**filter()**` → **select** items
- ✅ `**reduce()**` → **combine** into one value