---
Created: 2025-06-05T07:02
---
variable scope = where a variable is visible and accessible  
scope resolution = (LEGB) Local -> Enclosed -> Global -> Built-in

```Python
"""
def func1():
    # Local
    x = 1
    print(x)

def func2():
    # Local
    x = 2
    print(x)

def func3():
    # enclosed
    x = 4
    def func4():
        # local
        # x = 5
        print(x)
    func4()

# Global
x = 3

func1()
func2()
func3()
"""

from math import e

def func1():
    e = 2
    print(e)

e= 3
func1()
```