---
Created: 2025-08-21T19:29
tags:
  - Introspection-&-Refleciton
---
## ✅ **What is** `**callable()**`**?**

`callable(obj)` checks if an object **can be called like a function**.

✔️ Returns **True** if `obj()` would work

✔️ Returns **False** if it’s not callable

---

## 🏗 **Basic Usage**

```Python
print(callable(len))         # ✅ True (functions are callable)
print(callable("hello"))     # ❌ False (string not callable)
print(callable(list))        # ✅ True (class constructors are callable)
```

---

## ✅ **What objects are callable?**

- **Functions**
- **Classes** (because calling creates an instance)
- **Objects with** `**__call__**` **method**

---

## 🔹 **Example: Class with** `**__call__**`

```Python
class Greeter:
    def __call__(self, name):
        return f"Hello {name}!"

g = Greeter()

print(callable(g))    # ✅ True
print(g("Alice"))     # ✅ Works like a function → "Hello Alice!"
```

➡ Any object with a `__call__` method becomes **callable**.

---

## ✅ **Why use** `**callable()**`**?**

- **Check before calling** to avoid `TypeError`
- Useful in APIs/plugins where you accept either **values or functions**

---

## ⚠️ **Gotchas**

- A class is callable because it **returns an instance** when called.
- `callable()` **does not check arguments**—just whether it can be called at all.

---

## 📌 **Summary Table**

|Object Type|callable?|
|---|---|
|Function|✅ Yes|
|Class|✅ Yes|
|Instance (no `__call__`)|❌ No|
|Instance with `__call__`|✅ Yes|
|String, int, list|❌ No|

---

## 🌍 **Real-World Example: Value or Function?**

```Python
def get_discount():
    return 0.1

discount = get_discount  # Could be a function
price = 100

# Allow either a number or a function
def final_price(price, discount):
    d = discount() if callable(discount) else discount
    return price * (1 - d)

print(final_price(price, 0.2))         # static discount
print(final_price(price, get_discount)) # dynamic discount
```

Output:

```Plain
80.0
90.0
```

👉 **Why** `**callable()**`**?**

- Lets you **accept either a plain value or a function** that computes it.

---

✅ **TL;DR:**

- `callable(obj)` → True if `obj()` can be called
- Functions, classes, and objects with `__call__` are callable
- Useful for **dynamic APIs** where you accept both values & callables