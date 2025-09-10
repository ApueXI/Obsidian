---
Created: 2025-06-05T06:22
---
```Python
def shipping_label(*args, **kwargs):
    for arg in args:
        print(arg, end=' ')
    print()
    
    if 'apt' in kwargs:
        print(f"{kwargs.get('street')}")
        print(f"{kwargs.get('apt')}")
        print(f"{kwargs.get('city')}")
        print(f"{kwargs.get('zipcode')}")
        print(f"{kwargs.get('country')}")

shipping_label('Doctor' , 'Laren', 'Acob', 'Ignacio', street='Villa Gracia', apt='1234', city='laguna',zipcode='5678',country='Philippines')
```