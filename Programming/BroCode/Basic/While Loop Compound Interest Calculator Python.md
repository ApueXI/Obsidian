---
Created: 2025-06-05T07:04
---
```Python
principle = 0
rate = 0
time = 0

while True:
    principle = float(input("Enter the principle amount : "))
    if principle <= 0:
        print("Principle cannot be less than or rqual to zero")
    else:
        break

while True:
    rate= float(input("Enter the interest rate : "))
    if rate <= 0:
        print("Interest rate cannot be less than or rqual to zero")
    else:
        break

while True:
    time = float(input("Enter the Time in years : "))
    if time <= 0:
        print("Time cannot be less than or rqual to zero")
    else:
        break

total = principle * pow((1 + rate / 100), time)

print(f"Balance after {time} year/s is ${total :.2f}")
```