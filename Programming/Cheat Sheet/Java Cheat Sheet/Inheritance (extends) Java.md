---
Created: 2025-08-25T19:57
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is Inheritance?

- **Inheritance** allows a **class (subclass/child)** to **reuse fields and methods** from another **class (superclass/parent)**.
- Promotes **code reusability** and **hierarchical relationships**.
- Declared using the `**extends**` keyword.

---

### 🔹 Syntax

```Java
class Parent {
    // fields and methods
}

class Child extends Parent {
    // additional fields and methods
}

```

- **Child class** inherits **all non-private members** of parent class.
- **Single inheritance** in Java (no multiple class inheritance).

---

### 🔹 Example

```Java
// Parent class
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

// Child class
class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();   // inherited from Animal
        dog.bark();  // own method
    }
}

```

✅ Output:

```Plain
Animal eats
Dog barks

```

- **Dog** inherits `**eat()**` from **Animal**.

---

### 🔹 Key Points

1. **Private members of parent class are NOT inherited.**
2. Constructors are **not inherited**, but a child can call them using `super()`.
3. A class can **extend only one class** (single inheritance).
4. Supports **multilevel inheritance**:

```Java
class Animal { }
class Dog extends Animal { }
class Puppy extends Dog { }

```

---

### 🔹 Using `super` Keyword

- **Access parent class members**: fields, methods, or constructors.

```Java
class Animal {
    String color = "White";

    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    String color = "Brown";

    void printColor() {
        System.out.println("Dog color: " + color);
        System.out.println("Animal color: " + super.color);
    }

    void eat() {
        super.eat(); // call parent method
        System.out.println("Dog eats bones");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.printColor();
        dog.eat();
    }
}

```

✅ Output:

```Plain
Dog color: Brown
Animal color: White
Animal eats
Dog eats bones

```

---

### 🔹 Gotchas / Notes

- Inheritance is **single by class** in Java.
- Use `**super()**` in constructor to call parent constructor.
- Avoid deep inheritance chains → can reduce code clarity.
- Supports **polymorphism** (child object can be treated as parent type).

---

## 2. 📊 Summary Table

|Concept|Syntax / Example|Notes|
|---|---|---|
|Inheritance|`class Child extends Parent`|Reuse fields & methods|
|Access parent members|`super.method()`|Call parent method|
|Access parent fields|`super.field`|Access hidden field|
|Multilevel inheritance|`A -> B -> C`|Single inheritance per class|
|Overriding|`childMethod()`|Child can redefine parent method|

---

### 🔹 Real-World Example

**Bank Accounts**

```Java
class BankAccount {
    protected double balance;

    public void deposit(double amount) {
        balance += amount;
    }

    public void showBalance() {
        System.out.println("Balance: " + balance);
    }
}

class SavingsAccount extends BankAccount {
    private double interestRate = 0.05;

    public void addInterest() {
        balance += balance * interestRate;
    }
}

public class Main {
    public static void main(String[] args) {
        SavingsAccount sa = new SavingsAccount();
        sa.deposit(1000);
        sa.addInterest();
        sa.showBalance(); // Balance: 1050.0
    }
}

```

- **SavingsAccount** inherits **deposit()** and **showBalance()** from **BankAccount**.