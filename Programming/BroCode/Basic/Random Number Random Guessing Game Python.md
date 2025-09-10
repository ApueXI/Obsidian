---
Created: 2025-06-05T07:00
---
```Python
import random

lowestNum = 1
highestNum = 100
guesses = 0
isRunnig = True

answer = random.randint(lowestNum, highestNum)

print("Python Number Guessing Game")
print(f"Select a Number betweeen {lowestNum} and {highestNum}")

while isRunnig:
    guess = input("Enter your guess : ")
    if guess.isdigit():
        guess = int(guess)
        guesses+=1
        if guess < lowestNum or guess > highestNum:
            print("That number is out of range")
            print(f"Please select a number betweeen {lowestNum} and {highestNum}")
        elif guess < answer:
            print("Too low, try again")
        elif guess > answer:
            print("Too high, try again")
        else:
            print(f"Correct, the answer was {answer}")
            print(f"Number of Guesses is : {guesses}")
            isRunnig = False
    else:
        print("Invalid Guess")
        print(f"Please select a number betweeen {lowestNum} and {highestNum}")
```