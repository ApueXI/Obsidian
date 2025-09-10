---
Created: 2025-06-05T06:44
---
```Python
num1 = float(input("Enter number 1                : "))
num2 = float(input("Enter number 1                : "))
operator = input("Pick an operator to use(+ - * /) : ")

if operator == "+":
    result = num1+num2
elif operator == "-":
    result = num1-num2
elif operator == "*":
    result = num1*num2
elif operator == "/":
    result = num1/num2
else:
    print("Invalid Input")
    
print(round(result, 2))

# wieght ocnverter

weight = float(input("Enter your wieght       : "))
unit = input("Enter the Unit (K or L) : ")

if unit == "K":
    weight *= 2.205
    unit = "Kgs"
    print(f"Your converted unit will be {weight}{unit}")
elif unit == "L":
    weight/= 2.505
    unit = "Lbs"
    print(f"Your converted unit will be {weight}{unit}")
else:
    print("Invalid Unit")


```