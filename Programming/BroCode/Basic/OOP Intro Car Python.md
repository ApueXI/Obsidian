---
Created: 2025-06-05T07:21
tags:
  - OOP
---
```Python
class Car:
    def __init__(self, model, year, color, is_sale):
        self.model = model
        self.year = year
        self.color = color        
        self.is_sale = is_sale

    def drive(self):
        print(f"You drive the {self.color} {self.model}")

    def stop(self):
        print(f"You stopped the {self.color} {self.model}")

    def describe(self):
        print(F"{self.year} {self.color} {self.model} {self.is_sale}")
```