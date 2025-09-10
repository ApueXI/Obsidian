---
Created: 2025-08-21T19:29
tags:
  - Module-&-Namespaces
---
## 1. What is `__name__`?

- Every Python module has a built-in attribute called `__name__`.
- When a module is **run directly**, `__name__` is set to `"__main__"`.
- When a module is **imported**, `__name__` is set to the module’s filename (without `.py`).

---

## 2. Purpose of `if __name__ == "__main__"`

- Used to **allow or prevent parts of code from running when the module is imported**.
- Code inside this `if` block runs **only when the file is executed directly**, not when imported.
- Useful for **testing**, **running scripts**, or **demo code** inside modules.

---

## 3. Basic Syntax

```Python
def main():
    print("Running as a script")

if __name__ == "__main__":
    main()
```

---

## 4. How It Works

- When you run `python mymodule.py`, `__name__ == "__main__"` is `True`, so `main()` runs.
- When you `import mymodule` in another script, `__name__ == "__main__"` is `False`, so `main()` is not executed automatically.

---

## 5. Real-World Example

File: `math_utils.py`

```Python
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

def main():
    print("Testing add:", add(2, 3))
    print("Testing multiply:", multiply(4, 5))

if __name__ == "__main__":
    main()
```

- Running `python math_utils.py` outputs:

```Plain
Testing add: 5
Testing multiply: 20
```

- But importing:

```Python
import math_utils
print(math_utils.add(10, 20))  # 30
```

does **not** print the test lines.

---

## Summary Table

|Concept|Description|Example|
|---|---|---|
|`__name__`|Module’s name attribute|`"__main__"` if run directly|
|`if __name__ == "__main__"`|Runs code only when module is executed directly|Used for testing/demo code|
|Use case|Prevents code from running on import|Separate script logic & importable code|