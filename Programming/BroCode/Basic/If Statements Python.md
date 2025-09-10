---
Created: 2025-06-05T06:44
---
```Python
age = int(input("Enter your age: "))

if age >= 18:
    print("You are now signed up")
elif age <= 0:
    print("You havent been born yet")
else:
    print("You must be 18+ plus to sign up")

response =  input("Would you like some food? (y/n) ")
if response == "y":
    print("You have received food")
else:
    print("You declined the food")


name = input("Please enter your name : ")

if name == "":
    print("You have not entered your name")
else:
    print(f"Welcome {name}")

is_Sale = True

if is_Sale:
    print("This product is on sale")
else:
    print("Thus product is not on sale")

"""
you can use "pass" as a placeholder
if is_Sale:
    pass
else:
    pass
"""    


    

# and → All conditions must be True

# or → At least one condition must be True

# not → Reverses the result (True becomes False and vice versa)
```