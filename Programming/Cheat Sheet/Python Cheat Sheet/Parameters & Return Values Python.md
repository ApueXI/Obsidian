---
Created: 2025-08-21T19:29
tags:
  - Function
---
### Parameters in Functions

Parameters are variables listed inside the parentheses in a function definition. They act as placeholders for the inputs your function needs.

---

### Types of Parameters

|Parameter Type|Syntax Example|Description|
|---|---|---|
|**Positional Parameters**|`def f(a, b):`|Arguments passed by position|
|**Default Parameters**|`def f(a=1, b=2):`|Parameters with default values|
|**Keyword-only Parameters**|`def f(*, a, b):`|Must be passed by keyword (Python 3+)|
|**Variable-length Positional (**`***args**`**)**|`def f(*args):`|Accepts any number of positional arguments|
|**Variable-length Keyword (**`****kwargs**`**)**|`def f(**kwargs):`|Accepts any number of keyword arguments|

---

### Parameter Examples

```Python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")              # Hello, Alice!
greet("Bob", "Hi")          # Hi, Bob!
```

```Python
def print_args(*args):
    for arg in args:
        print(arg)

print_args(1, 2, 3)
```

```Python
def print_kwargs(**kwargs):
    for key, value in kwargs.items():
        print(f"{key} = {value}")

print_kwargs(name="Alice", age=30)
```

---

### Return Values

- The `return` statement sends a result back from the function to where it was called.
- If no `return` is present, the function returns `None` by default.

---

### Return Value Examples

```Python
def add(a, b):
    return a + b

result = add(3, 4)   # result = 7
```

```Python
def divide(a, b):
    if b == 0:
        return None
    return a / b
```

---

### Returning Multiple Values

- Functions can return multiple values as a tuple.

```Python
def stats(numbers):
    return min(numbers), max(numbers), sum(numbers)/len(numbers)

low, high, avg = stats([1, 3, 5, 7, 9])
print(low, high, avg)   # 1 9 5.0
```

---

### Summary Table

|Concept|Syntax / Example|Description|
|---|---|---|
|Positional parameters|`def f(a, b):`|Parameters passed by position|
|Default parameters|`def f(a=1, b=2):`|Parameters with default values|
|Variable positional args|`def f(*args):`|Accept any number of positional arguments|
|Variable keyword args|`def f(**kwargs):`|Accept any number of named arguments|
|Return value|`return value`|Return value from function|
|Multiple return values|`return a, b, c`|Return multiple values as tuple|

---

### Real-World Example: User Profile Function

```Python
def create_profile(name, age=None, **additional_info):
    profile = {
        "name": name,
        "age": age,
    }
    profile.update(additional_info)
    return profile

user = create_profile("Alice", age=30, location="NY", profession="Engineer")
print(user)
```

**Output:**

```Python
{'name': 'Alice', 'age': 30, 'location': 'NY', 'profession': 'Engineer'}
```