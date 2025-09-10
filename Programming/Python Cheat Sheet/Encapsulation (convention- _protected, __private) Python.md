---
Created: 2025-08-21T19:29
tags:
  - OOP
---
## 1. What is Encapsulation?

- Encapsulation is an **OOP principle** that restricts direct access to some components (attributes/methods) of an object.
- It helps **hide internal state** and **protect data integrity**.
- Python uses **naming conventions** instead of strict access modifiers like `private` or `protected` in other languages.

---

## 2. Naming Conventions for Access Control

|Naming Style|Meaning|Behavior|
|---|---|---|
|`_single_leading_underscore`|**Protected (convention)**|Intended for internal use; still accessible, but signals "use with care"|
|`__double_leading_underscore`|**Private (name mangling)**|Name mangled to prevent accidental access outside class|
|`__double_leading_and_trailing_underscore__`|Special methods (dunder)|Python-defined special methods (not for access control)|

---

## 3. Protected Attributes (`_attribute`)

- By convention, attributes prefixed with a single underscore (`_`) are **protected**.
- Meant for **internal use** only.
- Accessible from outside but should be treated as non-public.

```Python
class MyClass:
    def __init__(self):
        self._protected_var = 42  # protected attribute
```

---

## 4. Private Attributes (`__attribute`)

- Attributes prefixed with **double underscore** (`__`) trigger **name mangling**.
- Python internally renames them to `_ClassName__attribute`.
- Prevents accidental access but **not true private** (can still be accessed if you know the mangled name).

```Python
class MyClass:
    def __init__(self):
        self.__private_var = 99  # private attribute

obj = MyClass()
# print(obj.__private_var)  # AttributeError
print(obj._MyClass__private_var)  # 99 (access via mangled name)
```

---

## 5. Why Use These Conventions?

- **Signal intent** to other programmers about attribute privacy.
- Reduce **namespace collisions** in subclasses (`__` name mangling helps).
- Avoid accidental modification or misuse.

---

## 6. Real-World Example: Bank Account

```Python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner             # public attribute
        self._balance = balance        # protected attribute (internal use)
        self.__password = "secret"    # private attribute (name mangled)

    def deposit(self, amount):
        if amount > 0:
            self._balance += amount

    def withdraw(self, amount, password):
        if password == self.__password:
            if amount <= self._balance:
                self._balance -= amount
                print(f"Withdrew {amount}")
            else:
                print("Insufficient funds")
        else:
            print("Invalid password")

acc = BankAccount("Alice", 1000)
print(acc.owner)            # Alice (public)
print(acc._balance)         # 1000 (protected, accessible but not recommended)
# print(acc.__password)     # AttributeError
print(acc._BankAccount__password)  # secret (private via name mangling)
```

---

## Summary Table

|Naming Convention|Access Level|Behavior|Example|
|---|---|---|---|
|`public_var`|Public|Fully accessible|`obj.var`|
|`_protected_var`|Protected (convention)|Accessible but intended internal use|`obj._var` (discouraged outside)|
|`__private_var`|Private (name mangled)|Name mangled, harder to access|`obj._ClassName__var`|