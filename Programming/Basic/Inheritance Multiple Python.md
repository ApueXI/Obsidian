---
Created: 2025-06-05T07:18
tags:
  - OOP
---
multiple inheritance = inherit from more than one parent class  
C(A, B)  
multilevel inheritance = inherit from a parent which inherits from another parent  
C(B) <- B(A) <- A

```Python
class Animal:
    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f"This {self.name} is eating")

    def sleep(self):
        print(f"This {self.name} is sleeping")

class Prey(Animal):
    def flee(self):
        print(f"This {self.name} is fleeing")

class Predator(Animal):
    def hunt(self):
        print(f"This {self.name} is hunting")

class Rabbit(Prey):
    pass

class Hawk(Predator):
    pass

class Fish(Predator, Prey):
    pass

rabbit = Rabbit("Bugs")
hawk = Hawk("Hawk")
fish = Fish("Nemo")

rabbit.flee()
rabbit.eat()
rabbit.sleep()
print()

hawk.hunt()
hawk.eat()
hawk.sleep()
print()

fish.flee()
fish.hunt()
fish.eat()
fish.sleep()
```