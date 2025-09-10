---
Created: 2025-06-05T06:36
---
```Python
"""
def add(num1, num2):
    z = num1 + num2
    return z
def subtract(num1, num2):
    z = num1 - num2
    return z
def multiply(num1, num2):
    z = num1 * num2
    return z
def divide(num1, num2):
    z = num1 / num2
    return z

print(multiply(5,10))
"""

# variablename:str 
# the :str makes it so the variable hints a string can be taken
# kinda like string myString;
# however the variable does not contain any value and you use it, it will lead to an error 

def create_name(first:str, last:str):
    first = first.capitalize()
    last = last.capitalize()
    return first + " " + last

fullname = create_name("Laren Jay","Acob")

print(fullname)

print(create_name("bro", 'code'))
```