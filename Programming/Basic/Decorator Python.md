---
Created: 2025-06-05T07:07
tags:
  - OOP
---
Decorator = A function that extends the behavior of another function  
w/o modifying the base function  
Pass the base function as an argument to the decorator  
  
@add_sprinkles  
get_ice_cream("vanilla")

```Python
def add_sprinkles(func):
    def wrapper(*args, **kwargs):
        print("You add sprinkles")
        func(*args, **kwargs)
    return wrapper

def add_fudge(func):
    def wrapper(*args, **kwargs):
        print("You add fudge")
        func(*args, **kwargs)
    return wrapper

@add_sprinkles
@add_fudge
def get_icecream(flavor):
    print(f"here is your {flavor} ice cream")

get_icecream("Vanilla")
```