---
Created: 2025-06-05T06:23
---
```Python
import math
friends = 5
# friends += 1
# friends -= 1
# friends *= 1
# friends /= 1

# To the power of 
friends **= 2 


x = 3.14
y = -4
z = 9 
b = 9.4

# Round of the Number
roundOffToSometinhg = round(x)

# Gives the absolute value
abosoluteValue = abs(y)

# Raise to the power of something
toThePowerOf = pow(z, 3)

# Finds the maximum value in the given set
maximumValue = max(x, y, z)
minimumValue = min(x, y, z)


print(roundOffToSometinhg)
print(abosoluteValue)
print(toThePowerOf)
print(maximumValue)
print(minimumValue)

# Exponential Constant is e
print(math.e)
print(math.pi)

# Finds the squareRoot 
squareRoot = math.sqrt(z)

# Will round up a float up
roundUp = math.ceil(b)

# Will round down a float
roundDown = math.floor(x)

print(z)
print(roundDown)


# Line

radius = float(input("Enter the radius of the circle"))

cirucmference = 2 * math.pi * radius

# Rounds off to the nearest decimal point, which at this example is 2
print(f"The cirucmference is {round(cirucmference, 2)}")


radius2 = float(input("Enter the radius of a crcle"))

area2 = math.pi * pow(radius, 2)

print(f"The area of the circle is {round(area2, 2)}")



a = float(input("Enter side A: "))
b = float(input("Enter side b: "))

c = math.sqrt(pow(a, 2) + pow(b, 2))

print(f"Side C equals {c}")
```