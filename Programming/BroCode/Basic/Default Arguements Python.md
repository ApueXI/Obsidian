---
Created: 2025-06-05T06:27
---
default arguments = A default value for certain parameters  
AF default is used when that argument is omitted  
make your functions more flexible, reduces # of arguments

1. positional
2. DEFAULT
3. Keyword,
4. Arbitrary

```Python
# deafult values, means you dont need to input the dicount and tax, only the list_price 
# if you want to use dewfault arugments, it has to come after the normal arguements
def net_price(list_price, dicount=0, tax=.05):
    return list_price * (1 - dicount) * (1 + tax)

# you can still assign a new value
print(net_price(500, 0.1, 0))
```