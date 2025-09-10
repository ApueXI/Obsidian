---
Created: 2025-06-05T06:54
---
```Python
is_Raining = True
temp = 25.6

if temp >= 30 or temp <= 0 or is_Raining:
    print("Do not go outside")
else:
    print("Go outside")

temp2 = 35
is_Sunny = True

if temp2 >=30 and is_Sunny:
    print("it is hot outside")
else:
    print("it is not hot outside")


if temp2 <=20 and not is_Sunny:
    print("it is cold outside")
else:
    print("It is sunny outside")
```