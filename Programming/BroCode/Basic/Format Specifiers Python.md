---
Created: 2025-06-05T06:34
---
format specifiers = {value: flags) format a value based on what  
(number)f = round to that many decimal places (fixed point)  
: (number) = allocate that many spaces  
03 allocate and zero pad that many spaces  
:<= left justify  
:> = right justify  
:^ center align  
+= use a plus sign to indicate positive value  
:= = place sign to leftmost position  
: = insert a space before positive numbers  
:, comma separator

  

```Python
price1 = 3.12159
price2 = -987.65
price3 = 12.34
price4 = 123456789

#(number)f = round to that many decimal places (fixed point)
print(f"Price 1 is {price1 :.2f}")

#03 allocate and zero pad that many spaces
print(f"Price 2 is {price2 :20}")

#03 allocate and zero pad that many spaces
print(f"Price 3 is {price2 :020}")

#:> = right justify
print(f"Price 4 is {price2 :>020}")

#:<= left justify
print(f"Price 5 is {price2 :<020}")

#:^ center align
print(f"Price 6 is {price2 :^020}")

#+ = use a plus sign to indicate positive value
print(f"Price 7 is {price3 :+}")

#:, comma separator for big numbers
print(f"Price 8 is {price4 :,}")

#:= = place sign to leftmost position
print(f"Price 9 is {price2 :=20}")
```