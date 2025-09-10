---
Created: 2025-06-17T08:31
---
```Python
foods = []
prices = []
total = 0

while True:
    foodToBuy = input("Enter a food to buy (press q to quit) : ")
    #.lower() ignores the upper cases
    if foodToBuy.lower() == "q" : 
        break
    else:
        priceOfTheFood = float(input(f"Enter the price of a {foodToBuy} : $"))
        foods.append(foodToBuy)
        prices.append(priceOfTheFood)

print("Your Cart")
i = 0
for food in foods:
    print(f"{food} - ${prices[i]:.02f}")
    i+=1

for price in prices:
    total+=priceOfTheFood

print(f"Total price of the Food is ${total:.02f}")
```