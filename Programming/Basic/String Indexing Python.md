---
Created: 2025-06-05T07:02
---
```Python
creditNumber = "1234-5678-9012-3456"

# access a character within a string
print(creditNumber[4])

# print(creditNumber[start : end]) access the elemeent you want, e.g. starting from index 0 to index 4, it will read index 0-4
# can also write it without the "start" and it will assume the first
print(creditNumber[:6])
print(creditNumber[5:10])

# start with a starting point and you can write without an end point and python will assume the last index to be read
print(creditNumber[5:])

# gets the last index, can also use -2, -3, -4, and so o
print(creditNumber[-1])

# count every x character of the string, x = 2 at this moment
# can write iwthout the starting and ending point and it will assume everythin
print(creditNumber[::2])

# count the last 4 digit in the string
print(creditNumber[-4:])

# reverse the string order
creditNumberReverse = creditNumber[::-1]
print(creditNumberReverse)
```