---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What Are Attributes?

- **Attributes** are variables that belong to **objects** or **classes**.
- They store data associated with the object or class.

---

## 2. Instance Attributes

- Belong to **individual objects** (instances).
- Defined usually inside the `__init__` method using `self`.
- Each object has its **own copy** of instance attributes.

```Python
class Dog:
    def __init__(self, name, age):
        self.name = name    # instance attribute
        self.age = age
```

---

## 3. Class Attributes

- Belong to the **class itself**, shared by **all instances**.
- Defined directly inside the class, outside any method.
- Accessed via class name or instance.

```Python
class Dog:
    species = "Canis familiaris"  # class attribute shared by all dogs
```

---

## 4. Access & Modify Attributes

```Python
dog1 = Dog("Buddy", 4)
dog2 = Dog("Lucy", 7)

print(dog1.name)       # Buddy (instance attribute)
print(dog1.species)    # Canis familiaris (class attribute)

dog1.age = 5           # Modify instance attribute
Dog.species = "Canis lupus"  # Modify class attribute for all

print(dog2.species)    # Canis lupus (changed for all)
```

---

## 5. Attribute Lookup Order

When you access `instance.attribute`, Python checks:

1. If the attribute exists in the **instance’s dictionary** (instance attribute).
2. Else, looks in the **class** and its parent classes (class attribute).

---

## 6. Overriding Class Attributes in Instances

```Python
dog1.species = "Doggo"  # This creates an instance attribute named species for dog1 only

print(dog1.species)  # Doggo
print(dog2.species)  # Canis lupus (still class attribute)
```

---

## Summary Table

|Attribute Type|Defined Where|Shared Across Instances?|Access Example|
|---|---|---|---|
|Instance Attribute|Inside methods via `self`|No, unique per instance|`obj.attr`|
|Class Attribute|Directly in class body|Yes, shared by all|`Class.attr` or `obj.attr`|

---

## Real-World Example: Library Book System

```Python
class Book:
    library_name = "City Library"  # class attribute shared by all books

    def __init__(self, title, author):
        self.title = title         # instance attribute
        self.author = author

book1 = Book("1984", "George Orwell")
book2 = Book("The Hobbit", "J.R.R. Tolkien")

print(book1.library_name)  # City Library
print(book2.library_name)  # City Library

Book.library_name = "Downtown Library"  # Change for all instances

print(book1.library_name)  # Downtown Library
print(book2.library_name)  # Downtown Library

book1.library_name = "Local Branch"  # Overrides only for book1

print(book1.library_name)  # Local Branch
print(book2.library_name)  # Downtown Library
```