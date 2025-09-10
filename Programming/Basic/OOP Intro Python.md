---
Created: 2025-06-05T07:20
tags:
  - OOP
---
object = A "bundle" of related attributes (variables) and methods (functions)  
Ex. phone, cup, book  
You need a "class" to create many objects  
class = (blueprint) used to design the structure and layout of an object  
exactly like contructors

```Python
from oop_TheIntroCar import Car

car1 = Car("Mustang", 2024, "Red", False)
car2 = Car("Toyota", 1999, "White", True)

print(car1.model)
print(car1.year)
print(car1.color)
print(car1.is_sale)
car1.drive()
car1.stop()
car1.describe()

print()
print(car2.model)
print(car2.year)
print(car2.color)
print(car2.is_sale)
car2.drive()
car2.stop()
car2.describe()
```