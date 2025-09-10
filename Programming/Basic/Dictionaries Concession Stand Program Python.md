---
Created: 2025-06-05T06:30
---
```Python
menu = {"pizza" : 3.00, 
        "nachos" : 4.50, 
        "popcorn" : 6.00, 
        "fries" : 2.50, 
        "chips" : 1.00, 
        "pretzel" : 3.50, 
        "soda" : 3.00, 
        "lemonade" : 4.25}

cart = []

total = 0

print("-------------------MENU-------------------")

for keysss, valuesss in menu.items():
    print(f"{keysss :10} : ${valuesss:.02f}")

print("------------------------------------------\n")

while True:
    food = input("Select an item (q to quit) : ")
    if food.lower() == "q":
        break
    elif menu.get(food.lower()) is not None:
        cart.append(food.lower())

for food in cart:
    total += menu.get(food)
    print(food, end=" ")

print(f"\nTotal is : ${total:.02f}")
```