---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `map()`

- Applies a **function** to each item of an iterable and returns a **map object** (iterator).
- Often used with `list()` to see the results.

### Syntax:

```Python
map(function, iterable, ...)
```

### Examples:

```Python
nums = [1, 2, 3]
squared = map(lambda x: x**2, nums)
print(list(squared))  # [1, 4, 9]
```

---

## 2. `filter()`

- Filters elements of an iterable using a **function that returns True/False**.
- Returns a **filter object** (iterator).

### Syntax:

```Python
filter(function, iterable)
```

### Examples:

```Python
nums = [1, 2, 3, 4, 5]
evens = filter(lambda x: x % 2 == 0, nums)
print(list(evens))  # [2, 4]
```

---

## 3. `zip()`

- Combines elements from multiple iterables into **tuples**.
- Stops at the **shortest iterable**.

### Syntax:

```Python
zip(iter1, iter2, ...)
```

### Examples:

```Python
names = ["Alice", "Bob", "Charlie"]
scores = [90, 85, 92]
print(list(zip(names, scores)))
# [('Alice', 90), ('Bob', 85), ('Charlie', 92)]
```

---

## 4. `eval()`

- Evaluates a **string as Python expression** and returns the result.
- **Be careful!** It can execute arbitrary code.

### Syntax:

```Python
eval(expression, globals=None, locals=None)
```

### Examples:

```Python
x = 10
print(eval("x + 5"))  # 15
print(eval("len('abc')"))  # 3
```

---

## 5. `exec()`

- Executes a **string of Python code** but **does NOT return a value**.
- Used for running dynamic code.

### Syntax:

```Python
exec(code, globals=None, locals=None)
```

### Examples:

```Python
code = "for i in range(3): print('Hello', i)"
exec(code)
# Hello 0
# Hello 1
# Hello 2
```

---

## 6. `callable()`

- Checks if an object is **callable** (like a function, class, or object with `__call__`).

### Syntax:

```Python
callable(obj)
```

### Examples:

```Python
print(callable(len))    # True
print(callable(42))     # False

class MyClass:
    def __call__(self):
        print("Called!")

c = MyClass()
print(callable(c))      # True
```

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`map()`|Apply function to all iterable items|`map(str, [1,2]) -> ['1','2']`|
|`filter()`|Keep items where function returns True|`filter(lambda x:x>0, [-1,2]) -> [2]`|
|`zip()`|Combine multiple iterables into tuples|`zip([1,2],[3,4]) -> [(1,3),(2,4)]`|
|`eval()`|Evaluate string as Python expression|`eval("2+3") -> 5`|
|`exec()`|Execute string as Python code|`exec("print('Hi')")`|
|`callable()`|Check if object is callable (like a func)|`callable(len) -> True`|

---

## Real-World Example: Processing Student Data

```Python
names = ["Alice", "Bob", "Charlie"]
scores = [82, 95, 67]

# Combine names and scores
students = list(zip(names, scores))
print("Students:", students)
# [('Alice', 82), ('Bob', 95), ('Charlie', 67)]

# Filter passing scores
passing = filter(lambda s: s[1] >= 70, students)
print("Passing:", list(passing))
# [('Alice', 82), ('Bob', 95)]

# Curve scores using map
curved = map(lambda s: (s[0], min(s[1] + 5, 100)), students)
print("Curved:", list(curved))
# [('Alice', 87), ('Bob', 100), ('Charlie', 72)]

# Dynamic evaluation
expr = "sum([score for _, score in students]) / len(students)"
print("Average:", eval(expr))
```