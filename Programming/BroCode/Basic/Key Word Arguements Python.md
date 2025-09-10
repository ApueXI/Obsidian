---
Created: 2025-06-05T06:45
---
keyword arguments = an argument preceded by an identifier  
helps with readability order of arguments doesn't matter  
1. positional 2. default 3. KEYWORD 4. arbitrary

```Python
def hello(greeting, title, firstN, lastN):
    print(f"{greeting} {title}{firstN} {lastN}")

# positional arguemnts should be first and keywords should be last,
# key words does not care about the position but positional arugments does
# keywords arguments can also be used to calirify variables
hello("Hello", firstN="Laren" , title="Sir.", lastN='Acob')

# end is also a keyword arguement
for x in range(1, 11):
    print(x, end=" ")

print('\n1', '2', '3', '4', '5', '6', '8', '9', sep="-")
```