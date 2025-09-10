---
Created: 2025-08-25T19:57
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is Polymorphism?

- **Polymorphism** = the ability of an **object to take many forms**.
- Allows **one interface (method)** to be used for **different underlying forms (objects)**.
- Two main types in Java:
    1. **Compile-time (Method Overloading)** – already covered.
    2. **Runtime (Method Overriding / Dynamic Polymorphism)** – focus here.

---

### 🔹 Method Overriding

- **Occurs when a subclass provides its own implementation** of a method already defined in the parent class.
- **Rules:**
    1. Method name, return type, and parameters **must be same**.
    2. Access modifier in child **cannot be more restrictive** than parent.
    3. Only **inherited methods** can be overridden.
    4. `**@Override**` **annotation** is recommended.

### Example:

```Java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Animal();
        a.sound(); // Animal makes a sound

        Dog d = new Dog();
        d.sound(); // Dog barks
    }
}

```

---

### 🔹 Dynamic Dispatch (Runtime Polymorphism)

- **The method to call is determined at runtime**, based on the **actual object**, not the reference type.

```Java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a;

        a = new Dog();
        a.sound(); // Dog barks

        a = new Cat();
        a.sound(); // Cat meows
    }
}

```

- **Reference type:** `Animal`
- **Actual object:** `Dog` or `Cat`
- JVM decides which `sound()` method to call at runtime → **dynamic dispatch**

---

### 🔹 Using `super` in Overriding

- Child can call **parent method** using `super.methodName()`

```Java
class Dog extends Animal {
    @Override
    void sound() {
        super.sound(); // call parent method
        System.out.println("Dog barks"); // add child behavior
    }
}

```

---

### 🔹 Gotchas / Notes

- Only **instance methods** can be overridden. **Static methods cannot** (they can be hidden).
- **Private, final, and static methods cannot be overridden**.
- Supports **polymorphic behavior** in **collections, method parameters, and APIs**.

---

## 2. 📊 Summary Table

|Concept|Syntax / Example|Notes|
|---|---|---|
|Method Overriding|`@Override void method()`|Redefine parent method in child|
|Dynamic Dispatch|`Parent ref = new Child(); ref.method();`|Method resolved at runtime|
|Calling Parent Method|`super.method()`|Access overridden method|
|Restrictions|Cannot override static/final/private methods|Only instance, non-final methods|

---

### 🔹 Real-World Example

**Bank Accounts with Polymorphism**

```Java
class BankAccount {
    double balance;

    void calculateInterest() {
        System.out.println("Generic interest calculation");
    }
}

class SavingsAccount extends BankAccount {
    @Override
    void calculateInterest() {
        System.out.println("Savings account interest: " + balance * 0.05);
    }
}

class FixedDepositAccount extends BankAccount {
    @Override
    void calculateInterest() {
        System.out.println("FD account interest: " + balance * 0.08);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc;

        acc = new SavingsAccount();
        acc.balance = 1000;
        acc.calculateInterest(); // Savings account interest: 50.0

        acc = new FixedDepositAccount();
        acc.balance = 1000;
        acc.calculateInterest(); // FD account interest: 80.0
    }
}

```

- Shows **runtime polymorphism**: same reference type, different actual objects → different behavior.