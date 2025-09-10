---
Created: 2025-08-21T19:29
tags:
  - Module-&-Namespaces
---
## 1. What is Scope?

- **Scope** defines the **visibility and lifetime of variables** in different parts of your code.
- Determines **where variables can be accessed or modified**.

---

## 2. LEGB Rule — The Order Python Looks Up Variables

Python resolves variables by searching these scopes **in order**:

|Letter|Scope Type|Description|
|---|---|---|
|L|**Local**|Names defined inside the current function or lambda.|
|E|**Enclosing**|Names in the local scopes of any enclosing functions (nested functions).|
|G|**Global**|Names defined at the top-level of a module or declared global using `global`.|
|B|**Built-in**|Names preassigned in the built-in Python module (like `print`, `len`).|

---

## 3. Example of Each Scope

```Python
x = "global x"  # Global scope

def outer():
    x = "enclosing x"  # Enclosing scope

    def inner():
        x = "local x"  # Local scope
        print(x)       # Prints "local x"

    inner()
    print(x)           # Prints "enclosing x"

outer()
print(x)               # Prints "global x"
print(len([1,2,3]))    # Built-in function
```

---

## 4. Modifying Variables in Different Scopes

- Use `global` to modify a **global** variable inside a function.
- Use `nonlocal` to modify an **enclosing (non-global)** variable inside nested functions.

```Python
count = 0  # global

def outer():
    count = 10  # enclosing

    def inner():
        nonlocal count
        count += 5  # modifies enclosing count
        print(count)

    inner()
    print(count)

outer()
print(count)
```

Output:

```Plain
15
15
0
```

---

## 5. Summary Table

|Scope|Where Defined|Access|Modify Keyword|
|---|---|---|---|
|Local (L)|Inside current function|Accessible inside function|No keyword needed|
|Enclosing (E)|In outer function(s)|Accessible inside nested funcs|`nonlocal`|
|Global (G)|At module level|Accessible anywhere in module|`global`|
|Built-in (B)|Python’s built-in namespace|Always accessible|Cannot modify|

---

## 6. Real-World Example: Counter with Nested Functions

```Python
def make_counter():
    count = 0  # enclosing variable

    def counter():
        nonlocal count
        count += 1
        return count

    return counter

c = make_counter()
print(c())  # 1
print(c())  # 2
print(c())  # 3
```