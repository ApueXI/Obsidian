---
Created: 2025-06-05T06:59
---
module = a file containing code you want to include in your program  
use 'import' to include a module (built-in or your own)  
useful to break up a large program reusable separate files

```Python
# module = a file containing code you want to include in your program 
#          use 'import' to include a module (built-in or your own) 
#          useful to break up a large program reusable separate files

"""
gives a list of modules available
print(help('modules'))

give the options you have access to
print(help('math'))

type import to use modules 
"""

"""
# as m, give the module math a kind of variable name
# import math as m

# another way to import
# brocode does not much use this as there can be name conflicts
from math import pi
"""

import modules_TheCreateMyOwnModules as example

result = example.pi
result = example.square(3)
result = example.cube(3)
result = example.circumference(3)
result = example.area(3)

print(result)
```