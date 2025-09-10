---
Created: 2025-08-21T19:29
tags:
  - Module-&-Namespaces
---
## 1. What is a Module?

- A **module** is any Python file ending with `.py`.
- You can **import** your own modules to reuse code across files.

---

## 2. Basic Import Syntax

Suppose you have two files in the same folder:

- `main.py`
- `mymodule.py`

`mymodule.py` contains:

```Python
def greet(name):
    print(f"Hello, {name}!")
```

In `main.py`, import and use:

```Python
import mymodule

mymodule.greet("Alice")  # Hello, Alice!
```

---

## 3. Import Specific Functions or Variables

```Python
from mymodule import greet

greet("Bob")  # Hello, Bob!
```

---

## 4. Import with Alias

```Python
import mymodule as mm

mm.greet("Charlie")  # Hello, Charlie!
```

---

## 5. Using Functions from Subfolders (Packages)

- A folder with an `__init__.py` file is treated as a **package**.
- Example folder structure:

```Plain
project/
│
├── main.py
└── utils/
    ├── __init__.py
    └── helpers.py
```

- In `helpers.py`:

```Python
def add(a, b):
    return a + b
```

- In `main.py`:

```Python
from utils.helpers import add

print(add(3, 4))  # 7
```

---

## 6. Adjusting `PYTHONPATH` or Using `sys.path`

If your module is in a different folder not recognized by Python, you can:

```Python
import sys
sys.path.append('/path/to/your/module/folder')

import yourmodule
```

---

## 7. Reloading Modules

If you modify a module during an interactive session, reload it:

```Python
import importlib
importlib.reload(mymodule)
```

---

## Summary Table

|Import Style|Syntax|Use Case|
|---|---|---|
|Import entire module|`import module_name`|Access with `module_name.func()`|
|Import specific names|`from module_name import func`|Direct access to `func()`|
|Import with alias|`import module_name as alias`|Shorter name `alias.func()`|
|Import from package|`from package.module import func`|Organized code in subfolders|
|Modify search path|`sys.path.append('path')`|Import modules outside cwd|

---

## Real-World Example: Calculator Module

File: `calculator.py`

```Python
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b
```

File: `main.py`

```Python
from calculator import add, multiply

print(add(5, 7))        # 12
print(multiply(3, 4))   # 12
```