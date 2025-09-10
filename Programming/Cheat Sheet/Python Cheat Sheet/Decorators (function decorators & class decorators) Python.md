---
Created: 2025-08-21T19:29
tags:
  - Advance-Topics
---
## ✅ **What are Decorators?**

Decorators are **higher-order functions** that **modify or enhance other functions or classes** without changing their source code.

- They **wrap** a function/class to add behavior before/after its execution.
- Widely used for logging, access control, memoization, timing, and more.

---

## 🏗 **1. Function Decorators**

### Basic Syntax

```Python
def decorator(func):
    def wrapper(*args, **kwargs):
        # Code before calling func
        print("Before function call")
        result = func(*args, **kwargs)
        # Code after calling func
        print("After function call")
        return result
    return wrapper

@decorator
def say_hello(name):
    print(f"Hello, {name}!")

say_hello("Alice")
```

Output:

```Plain
Before function call
Hello, Alice!
After function call
```

### Explanation:

- `@decorator` is syntax sugar for `say_hello = decorator(say_hello)`.
- The **wrapper** function controls behavior around the original function.

---

## ✅ **Common Uses of Function Decorators**

- Logging
- Authentication/Authorization
- Caching/memoization
- Timing function execution
- Validation

---

## 🏗 **2. Class Decorators**

Class decorators take a **class object** and return a modified or new class.

### Basic Syntax

```Python
def class_decorator(cls):
    class WrappedClass:
        def __init__(self, *args, **kwargs):
            self.instance = cls(*args, **kwargs)

        def __getattr__(self, attr):
            print(f"Accessing {attr}")
            return getattr(self.instance, attr)

    return WrappedClass

@class_decorator
class MyClass:
    def greet(self):
        print("Hello!")

obj = MyClass()
obj.greet()
```

Output:

```Plain
Accessing greet
Hello!
```

---

## ✅ **Function vs Class Decorators**

|Feature|Function Decorator|Class Decorator|
|---|---|---|
|Input|Function|Class|
|Output|Wrapped function|Wrapped class|
|Use cases|Modify function behavior|Modify/augment class behavior|
|Syntax|`@decorator` above function|`@decorator` above class|

---

## ⚠️ **Gotchas**

- Use `functools.wraps` in function decorators to preserve function metadata (name, docstring).
- Class decorators must handle all methods and attributes properly (commonly via `__getattr__`).

---

## 📌 **Summary Table**

|Concept|Description|
|---|---|
|**Function decorator**|Wraps function to add behavior|
|**Class decorator**|Wraps class to add behavior|
|`@decorator` syntax|Syntactic sugar to apply decorator|

---

## 🌍 **Real-World Example: Timing Function Execution**

```Python
import time
from functools import wraps

def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer
def waste_time(seconds):
    time.sleep(seconds)

waste_time(1.5)
```

Output:

```Plain
waste_time took 1.5008 seconds
```

---

✅ **TL;DR:**

- Decorators **wrap functions or classes** to add extra behavior.
- Function decorators wrap functions; class decorators wrap classes.
- Use `@decorator` syntax to apply.
- Use `functools.wraps` for better function decorators.