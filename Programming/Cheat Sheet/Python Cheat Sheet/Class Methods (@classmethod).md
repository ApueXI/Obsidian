---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is a Class Method?

- A **class method** receives the **class itself** (`cls`) as the first parameter instead of the instance (`self`).
- Decorated with `@classmethod`.
- Can access or modify **class state** that applies across all instances.
- Often used for **alternative constructors** or methods that affect the class as a whole.

---

## 2. Basic Syntax

```Python
class MyClass:
    @classmethod
    def my_class_method(cls, args):
        # code using cls
```

---

## 3. How It Works

- When called, Python passes the **class object** as `cls`.
- Can call other class methods or modify class attributes via `cls`.
- Can be called on the class itself or instances.

---

## 4. Example: Alternative Constructor

```Python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def from_birth_year(cls, name, birth_year):
        age = 2025 - birth_year
        return cls(name, age)

p = Person.from_birth_year("Alice", 1990)
print(p.name, p.age)  # Alice 35
```

---

## 5. Difference Between `@classmethod` and `@staticmethod`

|Feature|`@classmethod`|`@staticmethod`|
|---|---|---|
|First arg|`cls` (class object)|No special first argument|
|Access|Can access/modify class state|No access to class or instance data|
|Use case|Alternative constructors, class-wide operations|Utility methods|

---

## 6. Real-World Example: Tracking Number of Instances

```Python
class Robot:
    count = 0  # class attribute

    def __init__(self, name):
        self.name = name
        Robot.increment_count()

    @classmethod
    def increment_count(cls):
        cls.count += 1

    @classmethod
    def how_many(cls):
        return cls.count

r1 = Robot("R2D2")
r2 = Robot("C3PO")

print(Robot.how_many())  # 2
print(r1.how_many())     # 2 (can be called from instance too)
```

---

## Summary Table

|Feature|Description|Example|
|---|---|---|
|Decorator|`@classmethod`||
|First parameter|`cls` (class)|`def method(cls, ...)`|
|Access class data|Yes|`cls.count += 1`|
|Called on|Class or instance|`Class.method()` or `obj.method()`|
|Common use|Alternative constructors, class-wide methods|`from_birth_year()`|