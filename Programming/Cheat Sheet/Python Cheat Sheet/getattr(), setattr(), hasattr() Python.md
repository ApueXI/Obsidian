---
Created: 2025-08-21T19:29
tags:
  - Introspection-&-Refleciton
---
## ✅ **What are they for?**

These built-in functions allow **dynamic attribute access** at runtime.

✔️ Useful when you don’t know the attribute name beforehand.

---

## 🏗 **1.** `**getattr(obj, name, default)**` **→ Get an attribute**

```Python
class Person:
    name = "Alice"

p = Person()

print(getattr(p, "name"))        # ✅ Alice
print(getattr(p, "age", 30))     # ✅ 30 (default if missing)
```

➡ If attribute doesn’t exist, returns `default` (or raises `AttributeError` if not given).

---

## 🏗 **2.** `**setattr(obj, name, value)**` **→ Set an attribute**

```Python
setattr(p, "age", 25)    # Dynamically add attribute
print(p.age)             # ✅ 25
```

➡ Equivalent to `p.age = 25`.

---

## 🏗 **3.** `**hasattr(obj, name)**` **→ Check if attribute exists**

```Python
print(hasattr(p, "name"))  # ✅ True
print(hasattr(p, "email")) # ❌ False
```

➡ Returns `True` if attribute exists, `False` otherwise.

---

## ✅ **Why use these?**

- Dynamic attribute names (from user input or config)
- Reflection / meta-programming
- Loading attributes from data files, JSON, etc.

---

## ✅ **Example: Dynamic Access**

```Python
fields = ["name", "age", "email"]

for f in fields:
    if hasattr(p, f):
        print(f, "=", getattr(p, f))
    else:
        setattr(p, f, "unknown")  # add missing attributes
```

---

## ⚠️ **Gotchas**

- `getattr()` will **call** `**__getattr__**` or `__getattribute__` if defined.
- Setting a non-existent attribute creates it **even if it wasn’t originally in the class**.
- `hasattr()` **suppresses exceptions** inside `__getattr__`, which can hide errors.

---

## 📌 **Summary Table**

|Function|What it does|
|---|---|
|`getattr(obj, name, default)`|Get attribute (default if missing)|
|`setattr(obj, name, value)`|Set or create attribute dynamically|
|`hasattr(obj, name)`|Check if attribute exists|

---

## 🌍 **Real-World Example: JSON → Object Loader**

```Python
class Config:
    def __init__(self):
        self.debug = True
        self.port = 8000

config_data = {"debug": False, "host": "localhost"}

cfg = Config()

for key, value in config_data.items():
    if hasattr(cfg, key):
        print(f"Updating {key}...")
    else:
        print(f"Adding {key}...")
    setattr(cfg, key, value)

print(cfg.debug)  # False (updated)
print(cfg.host)   # localhost (newly added)
```

👉 **Why use dynamic access?**

- You can **update attributes from external data** without hardcoding their names.

---

✅ **TL;DR:**

- `getattr()` → get attribute safely (with optional default)
- `setattr()` → dynamically set or add an attribute
- `hasattr()` → check if attribute exists