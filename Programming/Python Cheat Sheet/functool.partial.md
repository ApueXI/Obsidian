---
Created: 2025-08-21T19:29
tags:
  - Functional-Programming-Features
---
## ✅ **What is** `**functools.partial**`**?**

`functools.partial` **pre-fills (binds) some arguments** of a function, creating a new function with fewer required parameters.

✔️ **Think of it as function customization.**

- You **freeze some arguments** → Get a **new callable**.
- Often used to simplify repetitive function calls.

---

## 🏗 **Basic Syntax**

```Python
from functools import partial

new_func = partial(original_func, arg1=value1, arg2=value2)
```

---

## 🔹 **Simple Example**

```Python
from functools import partial

def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
cube   = partial(power, exp=3)

print(square(5))  # 25
print(cube(2))    # 8
```

---

## 🧰 **When to Use** `**partial**`

- To **fix default arguments** without redefining the function
- To **create specialized versions** of a general function
- To **adapt existing APIs** for callbacks (e.g., GUI/event handlers)
- To **reduce repetitive code**

---

## ✅ **Common Uses**

🔹 **Preconfiguring** `**int()**` **for different bases**

```Python
bin_to_int = partial(int, base=2)
print(bin_to_int("1010"))  # 10
```

🔹 **For Callbacks (e.g., GUI)**

```Python
import tkinter as tk
from functools import partial

def greet(name):
    print(f"Hello, {name}!")

root = tk.Tk()
btn = tk.Button(root, text="Greet Alice", command=partial(greet, "Alice"))
btn.pack()
root.mainloop()
```

🔹 **With Higher-Order Functions**

```Python
from functools import partial
from operator import mul

double = partial(mul, 2)
print(list(map(double, [1, 2, 3])))  # [2, 4, 6]
```

---

## ⚠️ **Gotchas**

❌ `partial` only **binds arguments**, it **doesn’t clone the function**

✅ The new function still calls the original one

❌ If you bind all arguments, it just becomes a function that takes no parameters

✅ Sometimes better to just use a normal `lambda` for clarity

---

## 🏎 **partial vs lambda vs closure**

|Feature|partial|lambda|closure|
|---|---|---|---|
|**Best for**|Pre-filling args|Quick inline funcs|Remembering state|
|**Keeps state?**|❌ No|❌ No|✅ Yes|
|**Readability**|✅ Clean for arg binding|✅ Good for short|✅ For complex state|
|**Can add logic?**|❌ No|✅ Yes|✅ Yes|

---

## 📌 **Summary Table**

|Concept|Quick Notes|
|---|---|
|**Definition**|Pre-fills arguments of a function|
|**Syntax**|`partial(func, fixed_args...)`|
|**Returns**|New callable with fewer required args|
|**Best for**|Preconfigured callbacks, reducing repetitive code|
|**Limitations**|Can’t add new logic—just binds arguments|

---

## 🌍 **Real-World Example: API Client Wrapper**

Imagine you have a generic API request function:

```Python
def api_request(base_url, endpoint, method="GET", headers=None):
    return f"{method} {base_url}/{endpoint} with headers {headers}"
```

You can preconfigure a **GitHub API client**:

```Python
from functools import partial

# Pre-bind GitHub base URL
github_request = partial(api_request, "https://api.github.com", headers={"Auth": "token"})

print(github_request("users/octocat"))
# GET https://api.github.com/users/octocat with headers {'Auth': 'token'}

print(github_request("repos/octocat/hello-world", method="POST"))
# POST https://api.github.com/repos/octocat/hello-world with headers {'Auth': 'token'}
```

👉 **Why partial?**

- Avoids repeating `base_url` & `headers` for every call
- Creates a specialized “GitHub client” without rewriting the function

---

✅ **TL;DR:**

- `functools.partial` **pre-fills arguments** to create a **specialized function**.
- Great for **callbacks, preconfigured APIs, and reducing boilerplate**.