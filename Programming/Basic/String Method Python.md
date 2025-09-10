---
Created: 2025-06-05T07:03
---
```Python
fName = input("Enter first name : ")
phoneNumber = input("Enter your phone number : ")

"""
to use the the help()
> Steps
open terminal (ctrl + `)
type in "python"
type help{str}
"""

# reads how many character is a string, includes space
result = len(fName)

# finds the index of where the character is
result2 = fName.find("r")

# Finds the last occurance of a character
result3 = fName.rfind("r")

# Frist Letter is Capitalzie
name2 = fName.capitalize()

# all capitalize
name3 = fName.upper()

# all lowercase
name4 = fName.lower()

# Returns a bool if string containes only a digit
name5 = fName.isdigit()

# Returns a bool is a string only contains alphabetical letters
name6 = fName.isalpha()

# count how many character are within the string
resultPhoneNumber = phoneNumber.count("-")

# replaces the character
phoneNumberRepalce = phoneNumber.replace("-", " space ")

print(f"the characters in your name is {result2}")

# print(phoneNumberRepalce)
fName = "Red"
help(str)
```