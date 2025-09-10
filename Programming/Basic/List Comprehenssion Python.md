---
Created: 2025-06-05T06:53
---
List comprehension = A concise way to create lists in Python  
Compact and easier to read than traditional loops  
[expression for value in iterable if condition]

```Python

"""
# instead of doing this 
singles = []

for a in range(0, 10):
    singles.append(a + 1)

print(singles)

# You can do this
doubles = [x * 2 for x in range(1, 11)]
tripples = [y * 3 for y in range(1, 11)]
squares = [z * z for z in range(1, 11)]

print(doubles)
print(tripples)
print(squares)
"""

"""
fruits = ['apple', 'orange', 'banana', 'coconut']

fruits = [fruit.upper() for fruit in fruits]
print(fruits)

# can be also be done like this
fruits = [fruit.upper() for fruit in ['apple', 'orange', 'banana', 'coconut']]
print(fruits)

# Gets the first letter of a string
fruitsChars = [fruit[0].capitalize() for fruit in ['apple', 'orange', 'banana', 'coconut']]
print(fruitsChars)
"""

"""
numbers = [1, -2, 3, -4, 5, -6, 7, -8]

positiveNums = [num for num in numbers if num >= 0]

negativeNums = [num for num in numbers if num < 0]

evenNumbers = [num for num in numbers if num % 2 == 0]

oddNumbers = [num for num in numbers if not num % 2 == 0]

print(oddNumbers)
"""

grades = [85, 42, 79, 90, 56, 61, 30]

passingGrade = [grade for grade in grades if grade >= 60]
print(passingGrade)
```