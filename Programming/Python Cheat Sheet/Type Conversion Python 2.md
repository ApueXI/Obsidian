---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. Overview

- **Type conversion functions** convert values from one type to another.
- Useful when you want to ensure data is in the correct format for operations.

---

## 2. Conversion Functions and Their Usage

|Function|Converts to|Typical Input Types|Example Usage|
|---|---|---|---|
|`int()`|Integer|Strings representing integers, floats (truncated), bools|`int("42") -> 42`, `int(3.9) -> 3`|
|`float()`|Float (decimal)|Strings representing floats, ints, bools|`float("3.14") -> 3.14`|
|`str()`|String|Any type|`str(100) -> "100"`|
|`bool()`|Boolean|Any type (empty sequences/zero => False)|`bool(0) -> False`, `bool([1]) -> True`|
|`list()`|List|Iterable (string, tuple, set, dict keys)|`list("abc") -> ['a','b','c']`|
|`tuple()`|Tuple|Iterable|`tuple([1,2]) -> (1,2)`|
|`set()`|Set (unordered unique)|Iterable|`set([1,1,2]) -> {1, 2}`|
|`dict()`|Dictionary|Iterable of key-value pairs, or mapping|`dict([('a',1), ('b',2)]) -> {'a':1, 'b':2}`|

---

## 3. Important Notes

- `int()` on a float **truncates** the decimal part (does not round).
- `bool()` returns `False` for: `None`, `False`, numeric zero (`0`, `0.0`), empty sequences/collections (`''`, `[]`, `{}`, `set()`), else `True`.
- `dict()` needs either another dictionary or iterable of key-value pairs (tuples or lists of length 2).
- `list()`, `tuple()`, and `set()` convert any iterable (including strings).

---

## 4. Examples

```Python
# int()
print(int("123"))        # 123
print(int(4.99))         # 4

# float()
print(float("3.14"))     # 3.14
print(float(5))          # 5.0

# str()
print(str(100))          # "100"
print(str([1, 2, 3]))    # "[1, 2, 3]"

# bool()
print(bool(0))           # False
print(bool("hello"))     # True
print(bool([]))          # False

# list()
print(list("hello"))     # ['h', 'e', 'l', 'l', 'o']
print(list((1, 2, 3)))   # [1, 2, 3]

# tuple()
print(tuple([1, 2, 3]))  # (1, 2, 3)
print(tuple("abc"))      # ('a', 'b', 'c')

# set()
print(set([1, 1, 2]))    # {1, 2}
print(set("hello"))      # {'h', 'e', 'l', 'o'}

# dict()
print(dict([('a', 1), ('b', 2)]))      # {'a': 1, 'b': 2}
print(dict({'x': 9, 'y': 8}))           # {'x': 9, 'y': 8}
```

---

## 5. Summary Table

|Function|Converts to|Input Example|Output Example|
|---|---|---|---|
|`int()`|Integer|`"42"`, `3.9`|`42`, `3`|
|`float()`|Float|`"3.14"`, `5`|`3.14`, `5.0`|
|`str()`|String|`100`, `[1, 2, 3]`|`"100"`, `"[1, 2, 3]"`|
|`bool()`|Boolean|`0`, `"hello"`, `[]`|`False`, `True`, `False`|
|`list()`|List|`"abc"`, `(1, 2, 3)`|`['a', 'b', 'c']`, `[1, 2, 3]`|
|`tuple()`|Tuple|`[1, 2, 3]`, `"abc"`|`(1, 2, 3)`, `('a', 'b', 'c')`|
|`set()`|Set|`[1, 1, 2]`, `"hello"`|`{1, 2}`, `{'h', 'e', 'l', 'o'}`|
|`dict()`|Dictionary|`[('a', 1), ('b', 2)]`, `{'x':9}`|`{'a':1, 'b':2}`, `{'x':9}`|

---

## 6. Real-World Example: Data Cleaning

```Python
data = ["10", "20", "30", "20", "10"]

# Convert to integers, remove duplicates, and sort
numbers = list(map(int, data))
unique_numbers = set(numbers)
sorted_numbers = sorted(unique_numbers)

print(sorted_numbers)  # Output: [10, 20, 30]
```