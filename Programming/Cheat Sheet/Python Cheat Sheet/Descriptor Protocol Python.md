---
Created: 2025-08-21T19:29
tags:
  - Advance-Topics
---
## ✅ **What is a Descriptor?**

A **descriptor** is any Python object that implements **at least one** of the following methods:

- `__get__(self, instance, owner)` → controls attribute **access**
- `__set__(self, instance, value)` → controls attribute **assignment**
- `__delete__(self, instance)` → controls attribute **deletion**

✔️ Used for **custom attribute behavior**

✔️ Core behind `@property`, classmethods, and staticmethods

---

## 🏗 **Basic Descriptor Example**

```Python
class MyDescriptor:
    def __get__(self, instance, owner):
        print("Getting value")
        return 42

    def __set__(self, instance, value):
        print(f"Setting value to {value}")
        instance._hidden = value

    def __delete__(self, instance):
        print("Deleting value")
        del instance._hidden

class MyClass:
    attr = MyDescriptor()

obj = MyClass()
print(obj.attr)     # Calls __get__
obj.attr = 100      # Calls __set__
del obj.attr        # Calls __delete__
```

Output:

```Plain
Getting value
Setting value to 100
Deleting value
```

---

## ✅ **Types of Descriptors**

1. **Data Descriptor** → defines `**__get__**` **AND** `**__set__**` **(or** `**__delete__**`**)**
    - Takes **priority over instance** `**__dict__**`
2. **Non-Data Descriptor** → defines only `**__get__**`
    - Can be **overridden by instance attributes**

---

## ✅ **When to Use Descriptors?**

- Type checking & validation
- Lazy loading attributes
- Computed attributes
- ORM fields (e.g., Django models)

---

## 🏎 **How It Works**

Accessing an attribute:

1. Python checks if it’s a **descriptor in the class**
2. If yes, it calls its `__get__`, `__set__`, or `__delete__` methods
3. If not, it falls back to **normal attribute lookup**

---

## ✅ **property = Descriptor!**

The built-in `property()` is a **descriptor** internally:

```Python
class Demo:
    def __init__(self):
        self._x = 0

    def get_x(self):
        return self._x

    def set_x(self, value):
        self._x = value

    x = property(get_x, set_x)

d = Demo()
d.x = 10   # Calls set_x()
print(d.x) # Calls get_x()
```

So `@property` is just a **convenient descriptor wrapper**.

---

## ⚠️ **Gotchas**

- **Descriptors only work at class level**, not instance level
- For data descriptors, **instance.dict doesn’t override them**
- Overuse can make code harder to read → prefer `@property` for simple cases

---

## 📌 **Summary Table**

|Method|Purpose|
|---|---|
|`__get__(self, instance, owner)`|Called on attribute access|
|`__set__(self, instance, value)`|Called on attribute assignment|
|`__delete__(self, instance)`|Called on attribute deletion|
|**Data Descriptor**|Has `__get__` + `__set__`/`__delete__`|
|**Non-Data Descriptor**|Has only `__get__`|

---

## 🌍 **Real-World Example: Type-Checked Attribute**

```Python
class TypedAttribute:
    def __init__(self, name, expected_type):
        self.name = name
        self.expected_type = expected_type

    def __get__(self, instance, owner):
        return instance.__dict__.get(self.name)

    def __set__(self, instance, value):
        if not isinstance(value, self.expected_type):
            raise TypeError(f"{self.name} must be {self.expected_type.__name__}")
        instance.__dict__[self.name] = value

class Person:
    name = TypedAttribute("name", str)
    age = TypedAttribute("age", int)

p = Person()
p.name = "Alice"     # ✅ OK
p.age = 30           # ✅ OK
p.age = "not a num"  # ❌ TypeError
```

👉 **Why Descriptors?**

- Centralized logic for **validation**
- Same descriptor reused for multiple attributes

---

✅ **TL;DR:**

- **Descriptors = objects that manage attribute access** via `__get__`, `__set__`, `__delete__`.
- `@property` is just a built-in **descriptor**.
- Use them for **validation, computed attributes, ORMs**.

Python