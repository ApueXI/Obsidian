---
Created: 2025-06-05T07:08
tags:
  - OOP
---
exception = An event that interrupts the flow of a program  
(ZeroDivisionError, TypeError, ValueError)

1. try,
2. except
3. finally

```Python
number = 0

while number != 1256:
    try:
        number = int(input("Enter a number : "))
        print(1 / number)

    except ZeroDivisionError:
        print("You cannot divide by zero")
    except ValueError:
        print("Enter only numbers")
    except Exception:
        print("This is bad practice as it catches all error but does not clarify the user what happened")
        print("Only use this as the last one")

    finally:
        print("Do some clean up here")
```