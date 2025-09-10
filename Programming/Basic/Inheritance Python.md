---
Created: 2025-06-05T07:17
tags:
  - OOP
---
Inheritance = Allows a class to inherit attributes and methods from another class  
Helps with code reusability and extensibility  
class Child(Parent)  
class Sub(Super)

```Python
class Animal:
    def __init__(self, name):
        self.name = name
        self.is_alive = True

    def eat(self):
        print(f"{self.name} is eating")

    def sleep(self):
        print(f"{self.name} is asleep")

class Dog(Animal):
    def speak(self):
        print("Wolf")

class Cat(Animal):
    def speak(self):
        print("Moew")

class Mouse(Animal):
    def speak(self):
        print("Squeek")

dog = Dog("Bronie")
cat = Cat("Spinx")
mouse = Mouse("Jerry")

print(dog.name)
print(dog.is_alive)
dog.eat()
dog.sleep()
dog.speak()
print()

print(cat.name)
print(cat.is_alive)
cat.eat()
cat.sleep()
cat.speak()
print()

print(mouse.name)
print(mouse.is_alive)
mouse.eat()
mouse.sleep()
mouse.speak()
```