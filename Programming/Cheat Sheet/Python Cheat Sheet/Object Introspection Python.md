---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `type()`

- Returns the **type (class)** of an object.
- Can also be used to dynamically create new classes (advanced).

### Syntax:

```Python
type(obj)
```

### Example:

```Python
print(type(42))         # <class 'int'>
print(type("hello"))    # <class 'str'>
print(type([1, 2]))     # <class 'list'>
```

---

## 2. `id()`

- Returns the **unique memory address (identity)** of an object during its lifetime.

### Syntax:

```Python
id(obj)
```

### Example:

```Python
x = 10
y = 10
print(id(x))            # e.g., 140709... (same as y because small ints are cached)
print(id(y))            # same ID as x
```

---

## 3. `isinstance()`

- Checks if an object is an **instance of a class** or a tuple of classes.

### Syntax:

```Python
isinstance(obj, class_or_tuple)
```

### Example:

```Python
print(isinstance(42, int))          # True
print(isinstance(3.14, (int, float)))  # True (matches float)
print(isinstance("hi", list))       # False
```

---

## 4. `issubclass()`

- Checks if a **class is a subclass** of another class (or tuple of classes).

### Syntax:

```Python
issubclass(class, class_or_tuple)
```

### Example:

```Python
class A: pass
class B(A): pass

print(issubclass(B, A))     # True
print(issubclass(A, B))     # False
print(issubclass(B, (A, dict)))  # True
```

---

## 5. `dir()`

- Returns a **list of valid attributes and methods** of an object.
- If no argument is given, returns names in the current local scope.

### Syntax:

```Python
dir(obj)
```

### Example:

```Python
print(dir([]))
# ['__add__', '__class__', '__contains__', ..., 'append', 'clear', 'copy', ...]

print(dir())  # shows current local names
```

---

## 6. `help()`

- Launches the **built-in help system** or shows the docstring of an object.

### Syntax:

```Python
help(obj)
```

### Example:

```Python
help(list)       # Shows documentation for the list class
help(str.upper)  # Shows documentation for the upper() method of str
```

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`type()`|Get an object’s type (class)|`type(42) -> <class 'int'>`|
|`id()`|Get unique memory ID of an object|`id("hi") -> 1407...`|
|`isinstance()`|Check if object is instance of class(es)|`isinstance(3.14, (int,float)) -> True`|
|`issubclass()`|Check if class is subclass of another|`issubclass(bool, int) -> True`|
|`dir()`|List attributes & methods of object|`dir([])` -> shows list methods|
|`help()`|Show docstring/help for object|`help(str)` -> shows string docs|

---

## Real-World Example: Debugging Objects

```Python
def debug_object(obj):
    print("Type:", type(obj))
    print("ID:", id(obj))
    print("Attributes/Methods:", dir(obj))
    print("Is string?", isinstance(obj, str))

# Test with different objects
debug_object([1, 2, 3])
debug_object("hello")

# Check subclass relationship
class Animal: pass
class Dog(Animal): pass

print("Is Dog a subclass of Animal?", issubclass(Dog, Animal))  # True

# Quick help
help(len)   # Shows docs for len()
```