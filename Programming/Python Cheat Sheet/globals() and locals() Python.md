---
Created: 2025-08-21T19:29
tags:
  - Module-&-Namespaces
---
## 1. What Are `globals()` and `locals()`?

- `globals()` returns a **dictionary** representing the current **global symbol table** — all global variables and functions accessible in the current module.
- `locals()` returns a **dictionary** representing the current **local symbol table** — variables and functions defined in the current local scope (inside a function or method).

---

## 2. Details

|Function|Returns|Scope|
|---|---|---|
|`globals()`|Dict of all global variables & functions|Module-level/global scope|
|`locals()`|Dict of local variables & functions|Current local scope (function, class, etc.)|

- In the **global scope**, `locals()` and `globals()` return the **same dictionary**.

---

## 3. Example Usage

```Python
x = 10  # global variable

def my_func():
    y = 20  # local variable
    print("locals():", locals())
    print("globals():", globals())

my_func()
```

Output:

```Plain
locals(): {'y': 20}
globals(): {'x': 10, 'my_func': <function my_func at 0x...>, ...}
```

---

## 4. Modifying Variables via `globals()` and `locals()`

- You **can modify** global variables by assigning to `globals()` dictionary.
- Modifying `locals()` inside a function **does NOT reliably affect local variables** (implementation dependent).

```Python
x = 5
globals()['x'] = 10
print(x)  # 10

def func():
    a = 1
    locals()['a'] = 2
    print(a)  # Still 1 (locals() modifications don't change actual local vars reliably)

func()
```

---

## 5. Use Cases

- **Debugging:** Inspect current variables.
- **Dynamic variable manipulation:** Add or change variables dynamically in global scope.
- **Metaprogramming:** Advanced use cases for frameworks or interpreters.

---

## Summary Table

|Function|Returns|Modifiable?|Typical Use Case|
|---|---|---|---|
|`globals()`|Global symbol table dictionary|Yes (affects global variables)|Access/modify global variables|
|`locals()`|Local symbol table dictionary|No (generally read-only)|Inspect local variables|

---

## Real-World Example: Using `globals()` to Dynamically Create Variables

```Python
def create_var(name, value):
    globals()[name] = value

create_var('new_var', 42)
print(new_var)  # 42
```