---
Created: 2025-06-05T07:24
tags:
  - OOP
---
super() = Function used in a child class to call methods from a parent class (superclass). #  
Allows you to extend the functionality of the inherited methods

```Python
class Shape:
    def __init__(self, color, is_filled):
        self.color = color
        self.is_filled = is_filled

    def describe(self):
        print(f"The color is {self.color} and the shape is {'filled' if self.is_filled else 'not fiiled'}")

class Circle(Shape):
    def __init__(self, color, is_filled, radius):
        super().__init__(color, is_filled)
        self.radius = radius

# method overriding
    def describe(self):
        super().describe()
        print(F"It is a circle with an area of {3.14159 * self.radius * self.radius}")

class Square(Shape):
    def __init__(self, color, is_filled, width):
        super().__init__(color, is_filled)
        self.width = width

class Triangle(Shape):
    def __init__(self, color, is_filled, width, height):
        super().__init__(color, is_filled)
        self.width = width
        self.height = height


circle = Circle("Red", True, 5)
square = Square("White", True, 10)
triangle = Triangle("Blue", False, 7, 14)

print(circle.color)
print(circle.is_filled)
print(circle.radius)
circle.describe()
print()

print(square.color)
print(square.is_filled)
print(square.width)
square.describe()
print()

print(triangle.color)
print(triangle.is_filled)
print(triangle.width)
print(triangle.height)
triangle.describe()
```