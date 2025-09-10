---
Created: 2025-06-05T07:01
---
```Python
import random
"""
unicode characters
         ●       ┌      ─      ┐      │      └      ┘ 
print("\u25CF \u250C \u2500 \u2510 \u2502 \u2514 \u2518 ")
"""

diceArt = {
    1 : ("┌─────────┐", 
         "│         │", 
         "│    ●    │", 
         "│         │", 
         "└─────────┘"),
    2 : ("┌─────────┐", 
         "│  ●      │", 
         "│         │", 
         "│      ●  │", 
         "└─────────┘"),
    3 : ("┌─────────┐", 
         "│  ●      │", 
         "│    ●    │", 
         "│      ●  │", 
         "└─────────┘"),
    4 : ("┌─────────┐", 
         "│  ●   ●  │", 
         "│         │", 
         "│  ●   ●  │", 
         "└─────────┘"),
    5 : ("┌─────────┐", 
         "│  ●   ●  │", 
         "│    ●    │", 
         "│  ●   ●  │", 
         "└─────────┘"),
    6 : ("┌─────────┐", 
         "│  ●   ●  │", 
         "│  ●   ●  │", 
         "│  ●   ●  │", 
         "└─────────┘")
}

dice = []
total = 0
numberOfDice = int(input("How many dice : "))

for die in range(numberOfDice):
    dice.append(random.randint(1, 6))

"""
# Vertical Print
for die in range(numberOfDice):
    for line in diceArt.get(dice[die]):
        print(line)
"""

# Horizontal print
for line in range(5):
    for die in dice:
        print(diceArt.get(die)[line], end="")
    print()

for die in dice:
    total+= die

print(f"Total is {total}")
```