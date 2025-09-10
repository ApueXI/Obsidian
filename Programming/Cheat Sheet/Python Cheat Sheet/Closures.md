---
Created: 2025-08-21T19:29
tags:
  - Functional-Programming-Features
---
## ✅ **What is a Closure?**

A **closure** is a function that remembers variables from its enclosing scope, even after the outer function has finished executing.

✔️ **3 conditions for a closure:**

1. There’s a nested (inner) function.
2. The inner function references variables from the outer function.
3. The outer function returns the inner function.

---

## 🏗 **Basic Structure**

```Python
def outer(x):
    def inner(y):
        return x + y
    return inner

closure_fn = outer(10)
print(closure_fn(5))  # 15 → remembers x=10
```

---

## 🧰 **When to Use Closures**

- **Data hiding** (like private variables)
- **Factory functions** (create functions with preconfigured behavior)
- **Callbacks & event handlers**
- **Avoiding global variables**

---

## 🔍 **Inspecting Closures**

```Python
print(closure_fn.__closure__)                 # tuple of cell objects
print(closure_fn.__closure__[0].cell_contents)  # 10
```

---

## ⚠️ **Common Gotchas**

❌ **Late binding issue in loops**

```Python
funcs = []
for i in range(3):
    funcs.append(lambda: i)

print(funcs[0]())  # 2, not 0!
```

✅ **Fix with default args**

```Python
funcs = []
for i in range(3):
    funcs.append(lambda i=i: i)
print(funcs[0]())  # 0
```

---

## 🏎 **Closures vs. Alternatives**

|Feature|Closure|Class|functools.partial|
|---|---|---|---|
|Keeps state?|✅ Yes|✅ Yes|✅ Yes (but immutable)|
|Lightweight?|✅|❌|✅|
|Extensible?|❌|✅|❌|
|Best for|Small stateful functions|Complex logic|Preconfigured functions|

---

## 📌 **Summary Table**

|Concept|Quick Notes|
|---|---|
|**Definition**|Function that remembers variables from its enclosing scope|
|**Needed for**|Data hiding, function factories, callbacks|
|**Key keywords**|`nonlocal` (to modify enclosed vars)|
|**Gotcha**|Late binding in loops|
|**Best alt.**|Classes for more complex state|

---

## 🌍 **Real-World Example: Web API Rate Limiter**

Imagine you’re building a **rate limiter** for an API call. A closure can remember the number of calls made.

```Python
def rate_limiter(limit):
    calls = 0
    def api_call():
        nonlocal calls
        if calls < limit:
            calls += 1
            return f"API Call {calls} successful"
        else:
            return "Rate limit exceeded"
    return api_call

# Create a limiter for 3 calls
limited_api = rate_limiter(3)

print(limited_api())  # API Call 1 successful
print(limited_api())  # API Call 2 successful
print(limited_api())  # API Call 3 successful
print(limited_api())  # Rate limit exceeded
```

👉 **Why closure?**

- Keeps `calls` hidden (no global variable)
- Each `limited_api` has its own independent state

---

✅ Next time you ask for a **cheat sheet**, I’ll always include:

- Full explanation
- Summary table
- Real-world example