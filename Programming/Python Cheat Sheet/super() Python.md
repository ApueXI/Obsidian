---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is `super()`?

- `super()` returns a **temporary object of the superclass** that allows you to call its methods.
- Commonly used in **inheritance** to call a parent class method from a child class.
- Helps to **avoid explicitly naming the parent class**, which supports easier code maintenance and multiple inheritance.

---

## 2. Basic Syntax

```Python
class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):
    def greet(self):
        super().greet()  # Call Parent’s greet()
        print("Hello from Child")
```

---

## 3. Why Use `super()`?

- To **reuse** or **extend** functionality from a parent class method.
- Avoid hardcoding the parent class name (better for multiple inheritance).
- Maintain **clean and maintainable** code.

---

## 4. Using `super()` with `__init__`

```Python
class Person:
    def __init__(self, name):
        self.name = name

class Employee(Person):
    def __init__(self, name, employee_id):
        super().__init__(name)   # Initialize name in Person
        self.employee_id = employee_id
```

---

## 5. `super()` in Multiple Inheritance

- In multiple inheritance, `super()` respects the **Method Resolution Order (MRO)**, calling the next method in line.

```Python
class A:
    def do_something(self):
        print("A")

class B(A):
    def do_something(self):
        super().do_something()
        print("B")

class C(A):
    def do_something(self):
        super().do_something()
        print("C")

class D(B, C):
    def do_something(self):
        super().do_something()
        print("D")

d = D()
d.do_something()
```

Output:

```Plain
A
C
B
D
```

---

## Summary Table

|Use Case|Description|Example|
|---|---|---|
|Call parent method|Reuse parent class behavior|`super().method()`|
|Initialize superclass|Call parent `__init__`|`super().__init__(args)`|
|Multiple inheritance|Calls next method in MRO|Supports diamond inheritance|

---

## Real-World Example: Shapes

```Python
class Shape:
    def __init__(self, color):
        self.color = color

    def describe(self):
        print(f"A {self.color} shape")

class Rectangle(Shape):
    def __init__(self, color, width, height):
        super().__init__(color)   # Initialize color in Shape
        self.width = width
        self.height = height

    def describe(self):
        super().describe()        # Call Shape's describe
        print(f"Rectangle of width {self.width} and height {self.height}")

rect = Rectangle("red", 10, 20)
rect.describe()
```

Output:

```Plain
A red shape
Rectangle of width 10 and height 20
```