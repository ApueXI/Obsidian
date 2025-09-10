---
Created: 2025-08-21T19:29
tags:
  - Advance-Topics
---
## ✅ **What is** `**__slots__**`**?**

By default, every Python object has a **dynamic** `**__dict__**` that stores its attributes.

- This allows adding attributes at runtime but **uses extra memory**.

`__slots__` **optimizes memory usage** by:

✔️ Restricting allowed attributes

✔️ Removing per-instance `__dict__` (and sometimes `__weakref__`)

---

## 🏗 **Basic Usage**

```Python
class Point:
    __slots__ = ("x", "y")  # Only allow these two attributes

    def __init__(self, x, y):
        self.x = x
        self.y = y

p = Point(1, 2)
p.x = 10  # ✅ Allowed
p.z = 5   # ❌ AttributeError: 'Point' object has no attribute 'z'
```

---

## ✅ **Why Use** `**__slots__**`**?**

- **Memory optimization**: avoids per-instance dictionaries
- **Faster attribute access** (sometimes)
- Prevents accidental new attributes

---

## 🔹 **What Happens Without** `**__slots__**`**?**

```Python
class Normal:
    def __init__(self):
        self.a = 1

n = Normal()
print(n.__dict__)  # {'a': 1}
```

With `__slots__`, there’s **no** `**__dict__**`:

```Python
class Slotted:
    __slots__ = ("a",)

s = Slotted()
s.a = 1
# print(s.__dict__)  # ❌ AttributeError
```

---

## ✅ **Key Rules**

1. **Slots must be a tuple/list of strings**
2. You can’t add new attributes not in `__slots__`
3. If you need **dynamic attributes**, don’t use `__slots__`
4. If you need weak references, add `"__weakref__"` to `__slots__`

---

## ⚠️ **Gotchas**

- Doesn’t always save memory for **small programs**—beneficial mainly for **many instances**
- Not inherited automatically → subclasses without `__slots__` get a `__dict__` again
- Can’t easily use `vars()` or inspect attributes dynamically

---

## 🏎 **slots vs normal class**

|Feature|Normal Class|With `__slots__`|
|---|---|---|
|Dynamic attrs|✅ Yes|❌ No (restricted)|
|Has `__dict__`|✅ Yes|❌ No (unless added)|
|Memory usage|Higher|Lower|
|Attribute speed|Normal|Slightly faster|

---

## 📌 **Summary Table**

|Feature|Behavior|
|---|---|
|`__slots__`|Tuple/list of allowed attribute names|
|Memory savings|✅ Yes (removes per-instance `__dict__`)|
|Dynamic attrs?|❌ No|
|Weak refs?|Add `"__weakref__"` manually|

---

## 🌍 **Real-World Example: Millions of Lightweight Objects**

```Python
class NormalPoint:
    def __init__(self, x, y):
        self.x = x
        self.y = y

class SlottedPoint:
    __slots__ = ("x", "y")
    def __init__(self, x, y):
        self.x = x
        self.y = y

import sys

normal = [NormalPoint(i, i) for i in range(100000)]
slotted = [SlottedPoint(i, i) for i in range(100000)]

print("NormalPoint memory:", sys.getsizeof(normal[0]))
print("SlottedPoint memory:", sys.getsizeof(slotted[0]))
```

👉 **Why** `**__slots__**`**?**

- When creating **millions of objects**, it reduces memory usage significantly
- Useful for **data models** (like in ORMs, simulation objects)

---

✅ **TL;DR:**

- `__slots__` **restricts attributes** & saves memory by removing `__dict__`
- Best for **large numbers of lightweight objects**
- Add `"__weakref__"` if needed