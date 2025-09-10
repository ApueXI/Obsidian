---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is Inheritance?

- Inheritance allows a **class (child/subclass)** to **inherit attributes and methods** from another class (parent/superclass).
- Enables **code reuse** and **hierarchical relationships** between classes.

---

## 2. Basic Syntax

```Python
class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):
    pass

c = Child()
c.greet()  # Output: Hello from Parent
```

---

## 3. Overriding Methods

- Child classes can **override** parent methods by redefining them.

```Python
class Child(Parent):
    def greet(self):
        print("Hello from Child")
```

---

## 4. Using `super()` to Call Parent Methods

- Use `super()` to **call a method from the parent class** inside the child.

```Python
class Child(Parent):
    def greet(self):
        super().greet()  # call Parent’s greet()
        print("and Hello from Child")
```

---

## 5. Multiple Inheritance

- A class can inherit from **multiple parent classes** (comma-separated).

```Python
class A:
    def method_a(self):
        print("A")

class B:
    def method_b(self):
        print("B")

class C(A, B):
    pass

c = C()
c.method_a()  # A
c.method_b()  # B
```

- Python uses **Method Resolution Order (MRO)** to determine which method to call if there's ambiguity.

---

## 6. Real-World Example: Animals

```Python
class Animal:
    def speak(self):
        print("Animal sound")

class Dog(Animal):
    def speak(self):
        print("Woof!")

class Cat(Animal):
    def speak(self):
        print("Meow!")

dog = Dog()
cat = Cat()

dog.speak()  # Woof!
cat.speak()  # Meow!
```

---

## Summary Table

|Concept|Description|Example|
|---|---|---|
|Single Inheritance|One parent class|`class Child(Parent):`|
|Method Overriding|Redefining parent methods|`def speak(self):`|
|`super()`|Call parent method|`super().method()`|
|Multiple Inheritance|Inheriting from multiple parents|`class C(A, B):`|
|MRO|Method Resolution Order (search order for methods)|`C.mro()` returns class order list|