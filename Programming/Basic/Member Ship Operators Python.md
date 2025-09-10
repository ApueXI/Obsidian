---
Created: 2025-06-05T06:58
---
Membership operators = used to test whether a value or variable is  
# found in a sequence  
# (string, list, tuple, set, or dictionary) 1  
# 1. in  
# 2. not in  
not is basically != in c#

```Python
"""
# String

word = 'APPLE'
letter = input("Guess the letter in the secret wordf : ").upper()

# in returns a bool 
if letter in word:
    print(f"There is a {letter}")
else:
    print(f"{letter} was not found")

if letter not in word:
    print(f"{letter} was not found")
else:
    print(f"There is a {letter}")
"""

"""
Sets
students = {'Acob', 'Goco', 'Andy'}

student = input("Enter the name of the student : ").capitalize()

if student in students:
    print(F'{student} was found')
else:
    print(f'{student} was not found')

if student not in students:
    print(f'{student} was not found')
else:
    print(F'{student} was found')
"""

"""
grades = {"Acob" : "A", "Goco" : "B", "Andy" : "S", "Zam" : "C"}

student = input("Enter the name of the student : ").capitalize()

if student in grades:
    print(f"{student}'s grade is  {grades[student]}")
else:
    print(f"{student} was not found")
"""

emal = "cabigan@gmail.com"

if "@" in emal and "." in emal:
    print("The email is correct")
else:
    print("Email is incorrect") 
```