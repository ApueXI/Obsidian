---
Created: 2025-06-05T07:00
---
```Python
import random
# print(help(random))

low = 1
high = 100

optionns = ("rock", "paper", "Scissors")

cards = ["2", "3", "4", "5", "6", "7", "8", "9", "A", "J", "Q", "K"]

# returns a random int from a given range
randomDiceNumber = random.randint(low, high)

# returns a random floating number from 0 to 1
numberFloatingToRandom=random.random()

# used for collections
rockPapaerScrissors = random.choice(optionns)

# shuffles a collection
random.shuffle(cards)

print(cards)
```