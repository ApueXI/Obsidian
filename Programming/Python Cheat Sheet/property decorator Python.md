---
Created: 2025-08-21T19:29
tags:
  - Advance-Topics
---
## ✅ **What is** `**@property**`**?**

`@property` turns a **method** into a **read-only attribute**, allowing you to access it like a normal attribute but still execute code behind the scenes.

✔️ Used for:

- **Encapsulation** (getter/setter)
- **Computed attributes**
- **Validation before setting values**

---

## 🏗 **Basic Usage**

```Python
class Circle:
    def __init__(self, radius):
        self._radius = radius  # underscore = “internal”

    @property
    def diameter(self):
        return self._radius * 2

c = Circle(5)
print(c.diameter)  # Access like attribute → 10

```

➡ `c.diameter` **calls the method** behind the scenes but looks like a simple attribute.

---

## 🔹 **Adding Setters and Deleters**

You can make a property **writable** by adding a setter.

```Python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

    @radius.setter
    def radius(self, value):
        if value <= 0:
            raise ValueError("Radius must be positive")
        self._radius = value

    @radius.deleter
    def radius(self):
        print("Deleting radius")
        del self._radius

c = Circle(5)
c.radius = 10       # Calls setter
print(c.radius)     # Calls getter → 10
del c.radius        # Calls deleter
```

---

## ✅ **Why Use** `**@property**`**?**

- Allows **computed values** without changing external API
- Provides **data validation** before setting attributes
- Keeps interface clean → `obj.attr` instead of `obj.get_attr()`

---

## ⚠️ **Gotchas**

- `@property` can’t take arguments
- Properties can be **overused** → better to use normal methods if logic is complex
- Don’t forget `@<property>.setter` if you want mutability

---

## 🏎 **property vs normal methods vs public attributes**

|Feature|property|normal method|attribute|
|---|---|---|---|
|Access style|`obj.attr`|`obj.method()`|`obj.attr`|
|Computed?|✅ Yes|✅ Yes|❌ No|
|Validation?|✅ Yes (via setter)|✅ Yes (inside method)|❌ No|

---

## 📌 **Summary Table**

|Decorator|Purpose|
|---|---|
|`@property`|Makes method a read-only attribute|
|`@<prop>.setter`|Allows setting value with validation|
|`@<prop>.deleter`|Allows deleting the attribute|

---

## 🌍 **Real-World Example: Temperature Converter**

```Python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self._celsius = value

    @property
    def fahrenheit(self):
        return (self._celsius * 9/5) + 32

t = Temperature(25)
print(t.celsius)      # 25
print(t.fahrenheit)   # 77.0 (computed)
t.celsius = -300      # Raises ValueError
```

👉 **Why** `**@property**`**?**

- `fahrenheit` is **computed dynamically**
- `celsius` has **validation** before setting

---

✅ **TL;DR:**

- `@property` makes methods **look like attributes**
- Add `@<prop>.setter` for writable attributes
- Great for **encapsulation & computed properties**