---
Created: 2025-08-23T20:10
tags:
  - Extra
---
# 🐍 Python Static Typing Cheat Sheet

---

## 1. Full Explanation

### 🔹 What is Static Typing in Python?

- Python is **dynamically typed** by default (types are checked at runtime).
- **Static typing** is optional, introduced via **type hints** (PEP 484, 2015).
- You declare expected types with `:` (for parameters/variables) and `>` (for return values).
- Tools like **mypy**, **Pyright**, or IDEs (PyCharm, VSCode) can **analyze types before runtime**.

---

### 🔹 Syntax Basics

```Python
def greet(name: str) -> str:
    return f"Hello, {name}"

```

- `name: str` → parameter `name` must be a `str`.
- `> str` → function returns a `str`.

---

### 🔹 Type Hints for Variables

```Python
age: int = 25
price: float = 19.99
active: bool = True
tags: list[str] = ["python", "typing"]

```

---

### 🔹 Common Typing Features

- **Union / Optional**
    
    ```Python
    from typing import Union, Optional
    def get_user(id: int) -> Union[str, None]:
        return None  # or a string
    
    def fetch_name(name: Optional[str]) -> str:
        return name or "Guest"
    
    ```
    
    `Optional[X]` is the same as `Union[X, None]`.
    
- **Any**
    
    ```Python
    from typing import Any
    data: Any = "could be anything"
    
    ```
    
- **Generics**
    
    ```Python
    from typing import List, Dict
    names: List[str] = ["Alice", "Bob"]
    scores: Dict[str, int] = {"Alice": 90, "Bob": 85}
    
    ```
    
- **Callable**
    
    ```Python
    from typing import Callable
    def process(fn: Callable[[int, int], int]) -> int:
        return fn(2, 3)
    
    ```
    
- **Type Aliases**
    
    ```Python
    UserId = int
    def get_user(uid: UserId) -> str:
        return f"User {uid}"
    
    ```
    
- **TypedDict & dataclass**
    
    ```Python
    from typing import TypedDict
    class User(TypedDict):
        id: int
        name: str
    
    user: User = {"id": 1, "name": "Alice"}
    
    ```
    

---

### 🔹 Checking Types

- **mypy** example:
    
    ```Bash
    pip install mypy
    mypy script.py
    
    ```
    
    If you pass wrong types, `mypy` warns you **before running the program**.
    

---

### 🔹 Gotchas

- Type hints **do not enforce types at runtime** – they’re for developers & tools.
- Use `isinstance()` if you need actual runtime checks.
- Python 3.9+ supports built-in generics (`list[str]`, `dict[str, int]`) instead of `typing.List`.
- Static typing improves **readability, debugging, refactoring, IDE autocomplete**.

---

## 2. Summary Table

|Feature|Syntax Example|Notes|
|---|---|---|
|Function param|`def f(x: int)`|Declares param type|
|Return type|`def f() -> str`|Declares return type|
|Variable hint|`age: int = 25`|Annotates variable|
|Union|`Union[int, str]`|Multiple types|
|Optional|`Optional[str]`|Shorthand for `Union[str, None]`|
|Any|`x: Any`|Disables type checking|
|List/Dict|`list[str]`, `dict[str, int]`|Generics (3.9+)|
|Callable|`Callable[[int, int], str]`|Function signature|
|Type Alias|`UserId = int`|Custom type name|
|TypedDict|`class User(TypedDict): ...`|Dict with fixed types|
|Check types|`mypy file.py`|Static analysis|

---

## 3. Real-World Example

Imagine building a **User Service** with static typing:

```Python
from typing import Optional, List, Dict

class User:
    def __init__(self, user_id: int, name: str, email: Optional[str] = None):
        self.user_id = user_id
        self.name = name
        self.email = email

class UserService:
    def __init__(self):
        self.users: Dict[int, User] = {}

    def add_user(self, user: User) -> None:
        self.users[user.user_id] = user

    def get_user(self, user_id: int) -> Optional[User]:
        return self.users.get(user_id)

    def get_all_names(self) -> List[str]:
        return [u.name for u in self.users.values()]

# Example usage
service = UserService()
service.add_user(User(1, "Alice", "alice@email.com"))
service.add_user(User(2, "Bob"))

print(service.get_user(1))         # ✅ returns User
print(service.get_user(3))         # ✅ returns None
print(service.get_all_names())     # ['Alice', 'Bob']

```

✅ Benefits:

- IDE autocompletion knows that `get_user` returns `Optional[User]`.
- If you forget to check `None`, `mypy` warns you.
- Safer refactoring, fewer runtime bugs.