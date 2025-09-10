---
Created: 2025-06-05T07:01
---
```Python
import random

options = ("rock", "paper", "scissor")
isGameRunnig = True

while isGameRunnig:
    
    computer = random.choice(options)
    player = None

    while player not in options: 
        player = input("Enter a choice (rock, paper, scissor) : ")

    print(f"Player   : {player}")
    print(f"Computer : {computer}")

    if player == computer:
        print("It is a tie")
    elif player == "rock" and computer == "scissor":
        print("You won")
    elif player == "paper" and computer == "rock":
        print("You won")
    elif player == "scissor" and computer == "paper":
        print("You won")
    else:
        print("You lost")

    if not input("Play again? (y/n) : ").lower() == "y":
        isGameRunnig = False

print("Thanks for playing")
```