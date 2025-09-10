---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is Method Overriding?

- **Method Overriding** happens when a **child (subclass)** provides its own implementation of a method that is already defined in its **parent (superclass)**.
- The child’s method **replaces** the parent’s method when called on the child object.
- Enables **polymorphism** and customization of inherited behavior.

---

## 2. Basic Syntax

```Python
class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):
    def greet(self):
        print("Hello from Child")

c = Child()
c.greet()  # Output: Hello from Child
```

---

## 3. Using `super()` in Overridden Methods

- Often, the child method calls the **parent’s method** inside it using `super()` to extend rather than completely replace behavior.

```Python
class Child(Parent):
    def greet(self):
        super().greet()  # call Parent greet()
        print("...and hello from Child")
```

---

## 4. Why Override Methods?

- To **change or extend behavior** in subclasses.
- To implement **specific versions** of a generic method defined in the parent class.

---

## 5. Real-World Example: Vehicles

```Python
class Vehicle:
    def start_engine(self):
        print("Engine started")

class Car(Vehicle):
    def start_engine(self):
        print("Car engine started with key")

class ElectricCar(Car):
    def start_engine(self):
        print("Electric car powered on silently")

v = Vehicle()
c = Car()
e = ElectricCar()

v.start_engine()  # Engine started
c.start_engine()  # Car engine started with key
e.start_engine()  # Electric car powered on silently
```

---

## Summary Table

|Feature|Description|Example|
|---|---|---|
|Override method|Redefine a parent class method in child class|`def method(self):`|
|Call parent method|Use `super()` to call the original parent method|`super().method()`|
|Purpose|Customize or extend inherited behavior||