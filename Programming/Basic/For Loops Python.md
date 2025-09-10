---
Created: 2025-06-05T06:30
---
```Python
for x in range(1, 11):
    print(x)

# add a comma and a number to count every x number, x = 2 at this case
for x in range(0, 11, 2):
    print(x)

for x in reversed(range(1, 11)):
    print(x)

creditCard = "1234-5678-9012-3456"
# iterates a string
for x in creditCard:
    print(x)

# use the continue to skip an interation
for x in range(1, 20):
    if x == 13:
        continue
    else:        
        print(x)

# for loops are used for iterating
```