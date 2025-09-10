---
Created: 2025-08-21T19:29
tags:
  - Introspection-&-Refleciton
---
## ✅ **What is Dynamic Attribute Handling?**

Dynamic attribute handling lets you **intercept attribute access** (get, set, delete) at runtime.

✔️ Useful for **custom behavior**, like lazy loading, proxies, or validation.

✔️ Implemented via special methods:

- `__getattr__()` → Fallback for missing attributes
- `__getattribute__()` → Intercepts **all** attribute access
- `__setattr__()` → Called when setting attributes
- `__delattr__()` → Called when deleting attributes

---

## 🏗 **1.** `**__getattr__(self, name)**` **→ Fallback for Missing Attributes**

Called **only if attribute is NOT found normally**.

```Python
class Demo:
    def __getattr__(self, name):
        print(f"{name} not found, returning default")
        return 42

d = Demo()
print(d.x)  # x not found → prints 42
```

---

## 🏗 **2.** `**__getattribute__(self, name)**` **→ Intercept ALL Access**

Called **for every attribute access**, even existing ones.

(Must use `super().__getattribute__` to avoid infinite recursion!)

```Python
class Demo:
    def __getattribute__(self, name):
        print(f"Accessing {name}")
        return super().__getattribute__(name)

    x = 10

d = Demo()
print(d.x)  # Logs: Accessing x → 10
```

---

## 🏗 **3.** `**__setattr__(self, name, value)**` **→ Intercept Setting Attributes**

Called whenever you do `obj.attr = value`.

```Python
class Demo:
    def __setattr__(self, name, value):
        print(f"Setting {name} to {value}")
        super().__setattr__(name, value)

d = Demo()
d.x = 100  # Logs: Setting x to 100
```

---

## 🏗 **4.** `**__delattr__(self, name)**` **→ Intercept Deletion**

Called when doing `del obj.attr`.

```Python
class Demo:
    def __delattr__(self, name):
        print(f"Deleting {name}")
        super().__delattr__(name)

d = Demo()
d.x = 1
del d.x  # Logs: Deleting x
```

---

## ✅ **Dynamic Attributes via** `**__dict__**`

You can **manipulate all attributes** in an object via `obj.__dict__`.

```Python
class Demo: pass
d = Demo()
d.__dict__["x"] = 99
print(d.x)  # 99
```

---

## ⚠️ **Gotchas**

- `__getattribute__()` is **always called**, so be careful to avoid recursion.
- `__getattr__()` is **only called if attribute is missing**.
- Always call `super().__setattr__` / `super().__getattribute__` for normal behavior.

---

## 📌 **Summary Table**

|Method|When called|
|---|---|
|`__getattr__`|Only for **missing attributes**|
|`__getattribute__`|**Every** attribute access|
|`__setattr__`|Whenever an attribute is set|
|`__delattr__`|Whenever an attribute is deleted|
|`__dict__`|Direct access to attributes|

---

## 🌍 **Real-World Example: Lazy Attribute Loading**

```Python
class LazyLoader:
    def __init__(self):
        self._cache = {}

    def __getattr__(self, name):
        print(f"Loading {name}...")
        value = f"Computed value for {name}"
        self._cache[name] = value
        return value

data = LazyLoader()

print(data.user)   # Loads lazily → "Computed value for user"
print(data.token)  # Loads lazily → "Computed value for token"
```

Output:

```Plain
Loading user...
Computed value for user
Loading token...
Computed value for token
```

👉 **Why?**

- Useful for **on-demand computation**, e.g., ORM fields, API calls, or caching.

---

✅ **TL;DR:**

- `__getattr__` → only for missing attributes
- `__getattribute__` → intercept ALL access
- `__setattr__` / `__delattr__` → intercept setting/deleting
- Use for **validation, lazy loading, proxies**