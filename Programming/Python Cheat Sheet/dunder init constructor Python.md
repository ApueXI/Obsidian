---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is `__init__`?

- `__init__` is a **special method** (a **dunder** = _double underscore_) in Python classes.
- It’s called **automatically when a new object is created**.
- Used to **initialize object attributes**.

---

## 2. Basic Syntax

```Python
class MyClass:
    def __init__(self, param1, param2):
        self.param1 = param1  # instance attribute
        self.param2 = param2

obj = MyClass("value1", "value2")
```

---

## 3. How It Works

- `__init__` is **not a true constructor** (object is already created by `__new__`), but it’s the **initializer**.
- It must have at least one parameter: `self` → refers to the current object.

---

## 4. Default & Optional Parameters

```Python
class Person:
    def __init__(self, name="Unknown", age=0):
        self.name = name
        self.age = age

p1 = Person()             # uses defaults → name="Unknown", age=0
p2 = Person("Alice", 25)  # custom values
```

---

## 5. Adding Logic in `__init__`

You can do validation, transformations, etc.:

```Python
class Temperature:
    def __init__(self, celsius):
        if celsius < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self.celsius = celsius
```

---

## 6. Multiple Constructors?

Python **does NOT support multiple** `**__init__**` **methods**, but you can use **default arguments** or **@classmethod** as an alternative:

```Python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    @classmethod
    def from_diameter(cls, diameter):
        return cls(diameter / 2)

c1 = Circle(5)
c2 = Circle.from_diameter(10)
```

---

## 7. `__init__` vs `__new__`

- `__new__` → actually **creates** the object
- `__init__` → **initializes** the object **after creation**

You rarely need `__new__` unless working with immutable types.

---

## Summary Table

|Feature|Description|Example|
|---|---|---|
|`__init__`|Runs after object creation|`def __init__(...)`|
|`self`|Refers to current object|`self.name = name`|
|Default parameters|Provide default values|`def __init__(self, x=0)`|
|Validation inside `__init__`|Can raise errors during initialization|`if x<0: raise ValueError()`|
|Alternative constructors|Use `@classmethod` to simulate multiple constructors|`from_diameter()`|

---

## Real-World Example: Car Class

```Python
class Car:
    def __init__(self, brand, model, year=2025):
        self.brand = brand
        self.model = model
        self.year = year

    def display_info(self):
        print(f"{self.year} {self.brand} {self.model}")

# Usage
car1 = Car("Tesla", "Model S")
car2 = Car("Toyota", "Corolla", 2020)

car1.display_info()  # 2025 Tesla Model S
car2.display_info()  # 2020 Toyota Corolla
```

✅ Demonstrates **default arguments**, **initialization**, and **methods**.