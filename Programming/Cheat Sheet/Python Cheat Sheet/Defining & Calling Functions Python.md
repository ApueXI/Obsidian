---
Created: 2025-08-21T19:29
tags:
  - Function
---
### What is a Function?

- A block of reusable code that performs a specific task.
- Defined once, can be called multiple times.

---

### Defining a Function

```Python
def function_name(parameters):
    """Optional docstring describing the function."""
    # function body
    return value  # optional
```

- `def` keyword starts the function definition.
- `function_name`: identifier for the function.
- `parameters`: inputs (optional).
- `return`: sends a result back to the caller (optional).

---

### Calling a Function

```Python
function_name(arguments)
```

- `arguments`: values passed to the function’s parameters.

---

### Detailed Features

- **Parameters and Arguments:**

```Python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")  # Alice is argument
```

- **Default Parameter Values:**

```Python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()       # Hello, Guest!
greet("Bob")  # Hello, Bob!
```

- **Return Values:**

```Python
def add(a, b):
    return a + b

result = add(3, 5)  # result = 8
```

- **Multiple Return Values:**

```Python
def powers(x):
    return x, x**2, x**3

a, b, c = powers(2)  # a=2, b=4, c=8
```

- **Keyword Arguments:**

```Python
def describe_pet(name, animal="dog"):
    print(f"{name} is a {animal}")

describe_pet(animal="cat", name="Whiskers")
```

- **Variable Number of Arguments:**

```Python
def sum_all(*numbers):
    return sum(numbers)

print(sum_all(1, 2, 3, 4))  # 10
```

- **Docstrings for Documentation:**

```Python
def square(x):
    """Return the square of x."""
    return x * x
```

---

### Summary Table

|Concept|Syntax / Example|Description|
|---|---|---|
|Define function|`def func_name(params):`|Starts a function definition|
|Call function|`func_name(args)`|Execute function with given arguments|
|Default parameters|`def f(x=10):`|Parameters with default values|
|Return value|`return value`|Send back value from function|
|Multiple returns|`return a, b, c`|Return multiple values as a tuple|
|Keyword arguments|`func_name(param=value)`|Call with named arguments|
|Variable arguments|`def f(*args):`|Accept any number of positional arguments|
|Docstring|`"""docstring"""`|Document function purpose|

---

### Real-World Example: Calculator Functions

```Python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b=1):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Division by zero"
    return a / b

print("Add:", add(10, 5))
print("Subtract:", subtract(10, 5))
print("Multiply:", multiply(10))
print("Divide:", divide(10, 2))
print("Divide by zero:", divide(10, 0))
```