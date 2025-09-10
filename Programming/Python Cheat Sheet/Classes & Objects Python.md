---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is a Class?

- A **class** is a **blueprint** for creating objects.
- It defines **attributes** (data) and **methods** (functions) that objects will have.

---

## 2. What is an Object?

- An **object** is an **instance** of a class.
- Each object has its own data (attributes) and can use the class’s methods.

---

## 3. Basic Class Syntax

```Python
class Person:
    # class attribute
    species = "Human"

    # constructor (initializer)
    def __init__(self, name, age):
        self.name = name    # instance attribute
        self.age = age

    # instance method
    def greet(self):
        print(f"Hi, I’m {self.name} and I’m {self.age} years old.")
```

---

## 4. Creating Objects

```Python
p1 = Person("Alice", 25)
p2 = Person("Bob", 30)

print(p1.name)  # Alice
print(p2.age)   # 30

p1.greet()      # Hi, I’m Alice and I’m 25 years old.
```

---

## 5. Class vs Instance Attributes

```Python
print(Person.species)  # "Human" (class attribute, shared)
print(p1.species)      # also "Human"

p1.species = "Alien"   # overrides only for p1
print(p1.species)      # Alien
print(p2.species)      # Human
```

---

## 6. Special Methods (a.k.a. Dunder Methods)

- `__init__` → constructor
- `__str__` → defines string representation of object
- `__repr__` → developer-friendly representation

Example:

```Python
class Car:
    def __init__(self, brand):
        self.brand = brand

    def __str__(self):
        return f"Car({self.brand})"

c = Car("Tesla")
print(c)  # Car(Tesla)
```

---

## 7. Class Methods & Static Methods

- **Instance method** → takes `self` (works on one object)
- **Class method** → takes `cls` (works on class itself)
- **Static method** → no `self` or `cls`, just a function inside class

```Python
class Math:
    @staticmethod
    def add(a, b):
        return a + b

print(Math.add(2, 3))  # 5
```

---

## Summary Table

|Concept|Description|Example|
|---|---|---|
|Class|Blueprint for objects|`class Person:`|
|Object|Instance of a class|`p = Person()`|
|Instance attribute|Belongs to a single object|`self.name`|
|Class attribute|Shared by all objects of a class|`species = "Human"`|
|`__init__`|Constructor (called when object is created)|`def __init__(...)`|
|`self`|Refers to the current object instance|`self.name = name`|
|Method types|Instance, Class (`@classmethod`), Static (`@staticmethod`)||

---

## Real-World Example: Bank Account

```Python
class BankAccount:
    bank_name = "Python Bank"  # class attribute

    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount
        print(f"Deposited {amount}. New balance: {self.balance}")

    def withdraw(self, amount):
        if amount > self.balance:
            print("Insufficient funds!")
        else:
            self.balance -= amount
            print(f"Withdrew {amount}. New balance: {self.balance}")

# Usage
acc = BankAccount("Alice", 100)
acc.deposit(50)     # Deposited 50. New balance: 150
acc.withdraw(200)   # Insufficient funds!
```

✅ Demonstrates **attributes**, **methods**, and **object behavior** in a real scenario.