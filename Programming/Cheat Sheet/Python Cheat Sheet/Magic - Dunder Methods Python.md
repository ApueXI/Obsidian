---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What are Magic (Dunder) Methods?

- Magic methods (also called **dunder methods** — double underscores before and after the name, e.g., `__init__`) are **special methods** Python uses to implement built-in behavior.
- They let you define or customize how objects behave with operators, built-in functions, and language constructs.

---

## 2. Common Magic Methods Categories

|Operation Type|Common Magic Methods|Purpose|
|---|---|---|
|Object Initialization|`__init__(self, ...)`|Initialize new object|
|Object Representation|`__str__(self)`, `__repr__(self)`|User/developer friendly string|
|Arithmetic Operations|`__add__(self, other)`, `__sub__`, etc.|Define behavior for `+`, `-`, etc.|
|Comparison Operators|`__eq__(self, other)`, `__lt__`, etc.|Define behavior for `==`, `<`, etc.|
|Container / Collection|`__len__(self)`, `__getitem__(self, key)`, `__setitem__`|Define length, indexing, assignment|
|Context Managers|`__enter__(self)`, `__exit__(self, exc_type, exc_val, exc_tb)`|Support `with` statement|
|Callable Objects|`__call__(self, ...)`|Make instances callable like functions|
|Iteration|`__iter__(self)`, `__next__(self)`|Make object iterable|

---

## 3. Examples of Key Magic Methods

### a) `__init__` — Initialization

```Python
class Person:
    def __init__(self, name):
        self.name = name
```

### b) `__str__` & `__repr__` — String Representations

```Python
class Person:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Person named {self.name}"

    def __repr__(self):
        return f"Person('{self.name}')"
```

### c) `__add__` — Overloading +

```Python
class Vector:
    def __init__(self, x, y):
        self.x, self.y = x, y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(v1 + v2)  # Vector(4, 6)
```

### d) `__len__` — Support len()

```Python
class Team:
    def __init__(self, members):
        self.members = members

    def __len__(self):
        return len(self.members)

team = Team(["Alice", "Bob", "Charlie"])
print(len(team))  # 3
```

---

## 4. Summary Table

|Magic Method|Purpose|Example Usage|
|---|---|---|
|`__init__(self, ...)`|Initialize new object|Called on creation|
|`__str__(self)`|Informal string representation|`print(obj)`|
|`__repr__(self)`|Official string representation|Interactive interpreter display|
|`__add__(self, other)`|Addition operator `+`|`obj1 + obj2`|
|`__eq__(self, other)`|Equality check `==`|`obj1 == obj2`|
|`__len__(self)`|Length of container|`len(obj)`|
|`__getitem__(self, key)`|Indexing operator `obj[key]`|`obj[0]`|
|`__setitem__(self, key, value)`|Assign item|`obj[0] = value`|
|`__iter__(self)`|Return iterator|Used in loops|
|`__next__(self)`|Iterator next element|Used in iterators|
|`__enter__(self)`|Enter context manager|Used with `with`|
|`__exit__(self, exc_type, exc_val, exc_tb)`|Exit context manager|Used with `with`|
|`__call__(self, ...)`|Make object callable|`obj()`|

---

## 5. Real-World Example: Custom Vector Class

```Python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"Vector({self.x}, {self.y})"

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(2, 3)
v2 = Vector(4, 1)

print(v1 + v2)  # Vector(6, 4)
print(str(v1))  # Vector(2, 3)
print(repr(v2)) # Vector(4, 1)
```