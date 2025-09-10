---
Created: 2025-06-05T06:36
---
```Python
def show_balance(balance):
    print(F"You balance is ${balance:.2f}")

def deposit():
    amount = float(input("Enter an amount to be deposited : "))

    if amount < 0:
        print("That is not a valid amount ")
        return 0
    else:
        return amount

def withdraw(balance):
    amount = float(input("Enter amount to be withdrawn : "))

    if amount > balance:
        print("Insufficient funds")
        return 0
    elif amount < 0:
        print("Amount must be greater than 0")
        return 0
    else:
        return amount


def main():
    balance = 0
    is_runnig = True

    while is_runnig:
        print("Banking program")
        print("1. Show Balance")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Exit")

        choice = input("Enter you choice (1, 2, 3, 4) : ")

        if choice == "1":
            show_balance(balance)
        elif choice == "2":
            balance += deposit()
        elif choice == "3":
            balance -= withdraw(balance)
        elif choice == "4":
            is_runnig = False
        else:
            print("The is not a valid choice")

    print("Thank you have a nice day")

if __name__ == '__main__':
    main()
```