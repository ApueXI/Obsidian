---
Created: 2025-06-05T07:04
---
```Python
name = input("Enter your name : ")

while name == "":
    print("You did not type your name")
    name = input("Enter your name : ")

print(f"Welcome {name}")

age = int(input("Enter your age : "))

while age < 0:
    print("Age cannot be negative")
    age = int(input("Enter your age : "))

print(f"You are {age} years old")
```