---
Created: 2025-06-05T06:43
---
continue key word skips the current iteration and starts from the begginning  
_ can be used im for loop, it says, for every iteration in range()

```Python
import random

def spin_row():
    symbols = ['⭐', '🔔', '🍎', '🍇', '🍉']

    return [random.choice(symbols) for _ in range(3)]

def print_row(row):
    print(" | ".join(row))

def pay_out(row, bet):
    if row[0] == row[1] == row[2]:
        if row[0] == '⭐':
            return bet * 3
        elif row [0] == '🔔':
            return bet * 4
        elif row [0] == '🍎':
            return bet * 5
        elif row [0] == '🍇':
            return bet * 6
        elif row [0] == '🍉':
            return bet * 20
    return 0

def main():
    start_balance = 100

    print("Welcome to Python SLots : ")
    print("Symbols ⭐ 🔔 🍎 🍇 🍉 ")

    while start_balance > 0:
        print(f"Current balance is : {start_balance}")

        bet = input("Place your bet amount : ")

        if not bet.isdigit():
            print("Please eneter a valid number")
            continue
        
        bet = int(bet)

        if bet > start_balance:
            print("Insufficinet funds")
            continue
        
        if bet <= 0:
            print("Bet must be over 0")
            continue    

        start_balance -= bet

        row = spin_row()

        print("Spinning>>>>\n")
        print_row(row)

        pay = pay_out(row, bet)

        if pay > 0:
            print(f"You won ${pay}")
        else:
            print("Sorry you won nothing")

        start_balance += pay

        if not input("Do you want to play again? (y/n) : ").lower() == 'y':
            break
        
    print(f"Game over your balance is : {start_balance}")

if __name__ == '__main__':
    main()
```