---
Created: 2025-08-21T19:29
tags:
  - Function
---
## 1. What Are Variable-length Arguments?

They allow functions to accept **any number of arguments**, making them more flexible.

- `args` → collects **extra positional arguments** as a **tuple**
- `*kwargs` → collects **extra keyword arguments** as a **dictionary**

---

## 2. Using `args` (Variable Positional Arguments)

```Python
def add_numbers(*args):
    return sum(args)

print(add_numbers(1, 2, 3))       # 6
print(add_numbers(5, 10, 15, 20)) # 50
```

✅ You can pass **0 or more** positional arguments.

✅ Inside the function, `args` is a **tuple**.

---

## 3. Using `*kwargs` (Variable Keyword Arguments)

```Python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key} = {value}")

print_info(name="Alice", age=30, location="NY")
```

✅ You can pass **0 or more** keyword arguments.

✅ Inside the function, `kwargs` is a **dictionary**.

---

## 4. Combining `args` and `*kwargs`

You can use both in the same function, but `*args` must come **before** `**kwargs`.

```Python
def example_func(*args, **kwargs):
    print("Positional:", args)
    print("Keyword:", kwargs)

example_func(1, 2, 3, name="Alice", age=25)
# Positional: (1, 2, 3)
# Keyword: {'name': 'Alice', 'age': 25}
```

---

## 5. Mixing with Normal Parameters

```Python
def greet(message, *names, punctuation="!"):
    for name in names:
        print(f"{message}, {name}{punctuation}")

greet("Hello", "Alice", "Bob", "Charlie", punctuation=".")
```

✅ Normal parameters first → `*args` → `**kwargs`

---

## 6. Argument Unpacking

You can **unpack lists/tuples into** `***args**` and **dicts into** `****kwargs**` when calling a function.

```Python
def introduce(name, age):
    print(f"My name is {name} and I'm {age} years old.")

data = ("Alice", 30)
introduce(*data)  # same as introduce("Alice", 30)

info = {"name": "Bob", "age": 25}
introduce(**info) # same as introduce(name="Bob", age=25)
```

---

## Summary Table

|Feature|Syntax / Example|Inside Function|Use Case|
|---|---|---|---|
|`*args`|`def f(*args)` → `f(1,2,3)`|Tuple|Variable **positional** args|
|`**kwargs`|`def f(**kwargs)` → `f(a=1, b=2)`|Dict|Variable **keyword** args|
|Both combined|`def f(*args, **kwargs)`|Tuple + Dict|Accept both types|
|Unpacking args|`f(*tuple_or_list)`|Tuple unpacking|Expand a sequence as args|
|Unpacking kwargs|`f(**dict)`|Dict unpacking|Expand dict as kwargs|

---

## Real-World Example: Flexible Logger

```Python
def log(message, *values, **options):
    level = options.get("level", "INFO")
    separator = options.get("sep", " | ")

    details = separator.join(str(v) for v in values)
    print(f"[{level}] {message}: {details}")

log("User login", "Alice", "IP 192.168.1.10", level="WARN", sep=" - ")
```

**Output:**

```Plain
[WARN] User login: Alice - IP 192.168.1.10
```

✅ Flexible logging with any number of details

✅ Keyword options for customization