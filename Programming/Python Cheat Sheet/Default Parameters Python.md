---
Created: 2025-08-21T19:29
tags:
  - Function
---
### What are Default Parameters?

- Parameters that have a default value assigned in the function definition.
- If an argument for that parameter is **not** provided when calling the function, the default value is used.
- Makes function calls more flexible and reduces the need for overloads.

---

### Syntax

```Python
def func(param1=default_value1, param2=default_value2):
    # function body
```

- Parameters with defaults **must come after** parameters without defaults.

---

### Examples

```Python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()            # Hello, Guest!
greet("Alice")     # Hello, Alice!
```

```Python
def power(base, exponent=2):
    return base ** exponent

print(power(3))        # 9  (3 squared)
print(power(3, 3))     # 27 (3 cubed)
```

---

### Important Notes

- Default parameter values are evaluated **once** at function definition time.
- Be careful when using **mutable default values** (like lists or dictionaries), as they can persist between calls.

```Python
def add_item(item, my_list=[]):
    my_list.append(item)
    return my_list

print(add_item(1))  # [1]
print(add_item(2))  # [1, 2]  (not reset!)
```

To avoid this, use `None` and set inside function:

```Python
def add_item(item, my_list=None):
    if my_list is None:
        my_list = []
    my_list.append(item)
    return my_list

print(add_item(1))  # [1]
print(add_item(2))  # [2]  (correctly reset)
```

---

### Summary Table

|Concept|Syntax / Example|Description|
|---|---|---|
|Define default parameter|`def f(a=1, b=2):`|Parameter with default value|
|Call function without param|`f()` or `f(a=5)`|Uses default if argument omitted|
|Mutable default caveat|Avoid mutable defaults like `[]`|Can cause shared state across calls|
|Correct mutable default use|Use `None` and assign inside function|Ensures new object every call|

---

### Real-World Example: Logging with Default Level

```Python
def log(message, level="INFO"):
    print(f"[{level}] {message}")

log("Server started")          # [INFO] Server started
log("Disk space low", level="WARN")  # [WARN] Disk space low

```