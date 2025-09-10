---
Created: 2025-06-05T06:39
---
Functions and classes in this module can be reused without the main block of code executing

Good practice (code is modular,

helps readability,

leaves no global variables,

avoid unintended execution)

Ex. library import library for functionality

When running library directly, display a help page

```Python
def fav_food(food):
    print(f"Your favorite food is {food}")


def main():
    print("This is script 1")
    fav_food("Pizza")
    print("Goodbye")

# means that if you are runnig this file, it will execute this
if __name__ == '__main__':
    main()
```