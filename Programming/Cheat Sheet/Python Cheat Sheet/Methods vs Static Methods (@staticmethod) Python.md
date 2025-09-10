---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. Instance Methods (Regular Methods)

- Automatically receive the **instance (**`**self**`**)** as the first parameter.
- Can access and modify **instance attributes** and call other instance methods.
- Most common method type in classes.

```Python
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):            # instance method
        print(f"Hello, my name is {self.name}")
```

---

## 2. Static Methods (`@staticmethod`)

- Defined inside the class but **do NOT receive** `**self**` **or** `**cls**` as parameters.
- Behave like **regular functions** but namespaced inside the class.
- Cannot access or modify instance or class state directly.
- Useful for utility functions related to the class.

```Python
class Math:
    @staticmethod
    def add(a, b):
        return a + b
```

---

## 3. When to Use Which?

|Method Type|When to Use|Can Access Instance Attributes?|Can Access Class Attributes?|
|---|---|---|---|
|Instance Method|Needs to work with object’s data (`self`)|Yes|Yes|
|Static Method|Independent utility function related to class|No|No|

---

## 4. Calling Methods

```Python
p = Person("Alice")
p.greet()             # Works, prints greeting

print(Math.add(5, 3)) # Works, prints 8
```

- Instance methods are called on objects (`p.greet()`).
- Static methods can be called on the class (`Math.add()`) or instances (`p.add()`), but they don’t get any special arguments.

---

## 5. Example Comparing Both

```Python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    def to_fahrenheit(self):          # instance method
        return (self.celsius * 9/5) + 32

    @staticmethod
    def is_valid_temp(temp):          # static method
        return -273.15 <= temp <= 1000
```

Usage:

```Python
temp = Temperature(25)
print(temp.to_fahrenheit())           # 77.0
print(Temperature.is_valid_temp(25)) # True
```

---

## Summary Table

|Feature|Instance Method|Static Method (`@staticmethod`)|
|---|---|---|
|Receives `self`|Yes|No|
|Can access object|Yes|No|
|Can access class|Yes|No|
|Called on|Object|Class or object|
|Use case|Behavior depending on object state|Utility functions related to class|

---

## Real-World Example: User Account Class

```Python
class User:
    def __init__(self, username):
        self.username = username

    def greet(self):  # instance method
        print(f"Welcome, {self.username}!")

    @staticmethod
    def is_valid_username(name):  # static method
        return isinstance(name, str) and len(name) >= 3

user = User("alice")
user.greet()                          # Welcome, alice!

print(User.is_valid_username("bob")) # True
print(User.is_valid_username(""))    # False
```