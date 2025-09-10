---
Created: 2025-08-21T19:29
tags:
  - Introspection-&-Refleciton
---
## ✅ **1.** `**type(obj)**` **→ Get the Type of an Object**

- Returns the **class/type** of an object.
- Useful for checking data types dynamically.

```Python
print(type(42))        # <class 'int'>
print(type("hello"))   # <class 'str'>
print(type([1,2,3]))   # <class 'list'>
```

✔️ You can also use it to **create new classes dynamically**:

```Python
MyClass = type("MyClass", (), {"x": 42})
obj = MyClass()
print(obj.x)  # 42
```

---

## ✅ **2.** `**id(obj)**` **→ Get Unique Memory Identifier**

- Returns an **integer** that is the object’s identity (usually its memory address).
- Two objects with the same `id()` are actually the **same object** in memory.

```Python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(id(a))  # e.g., 140210593830144
print(id(b))  # same as a → same object
print(id(c))  # different → new object
```

✔️ Helps you see if two variables **reference the same object**.

---

## ✅ **Checking Object Identity**

```Python
x = 256
y = 256
print(id(x) == id(y))  # True (Python caches small ints)

a = 1000
b = 1000
print(id(a) == id(b))  # Might be False (different objects)
```

---

## ✅ **Why use** `**type()**` **&** `**id()**`**?**

- `type()` → **Type checking**, reflection, dynamic class creation
- `id()` → **Debugging references**, checking **object identity**

---

## ⚠️ **Gotchas**

- `type()` is **not** the same as `isinstance()` (use `isinstance()` for inheritance).
- `id()` **only guarantees uniqueness during the object’s lifetime**, not after it’s deleted.

---

## 📌 **Summary Table**

|Function|What it does|
|---|---|
|`type(obj)`|Returns the class/type of the object|
|`id(obj)`|Returns a unique identifier (memory address)|
|`isinstance(obj, cls)`|Checks if obj is instance of cls (better for inheritance)|

---

## 🌍 **Real-World Example: Debugging Object References**

```Python
class User:
    pass

u1 = User()
u2 = u1
u3 = User()

print("u1 type:", type(u1))
print("u1 id:", id(u1))
print("u2 id:", id(u2))
print("u3 id:", id(u3))

print("u1 and u2 are same?", id(u1) == id(u2))  # True
print("u1 and u3 are same?", id(u1) == id(u3))  # False
```

Output:

```Plain
u1 type: <class '__main__.User'>
u1 id: 140256305580048
u2 id: 140256305580048
u3 id: 140256305580400
u1 and u2 are same? True
u1 and u3 are same? False
```

👉 **Why?**

- Helps debug when two variables point to **the same object** vs **different objects**.

---

✅ **TL;DR:**

- `type(obj)` → get class/type
- `id(obj)` → get unique memory ID
- Use `isinstance()` if you care about **inheritance checks**