---
Created: 2025-08-25T19:59
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is an Abstract Class?

- An **abstract class** is a class that **cannot be instantiated** directly.
- Can have:
    - **Abstract methods** (no body, must be implemented by subclass)
    - **Concrete methods** (normal methods with body)
    - **Fields** (variables)
- Declared using the keyword: `abstract`

---

### 🔹 What is an Abstract Method?

- A method **without implementation** (no `{}` body).
- Must be **overridden in a concrete subclass**.

```Java
abstract class Animal {
    // Abstract method
    abstract void sound();

    // Concrete method
    void eat() {
        System.out.println("Animal eats");
    }
}

```

---

### 🔹 Creating a Subclass

- A **subclass of an abstract class** must **implement all abstract methods**, or it must also be declared abstract.

```Java
class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        // Animal a = new Animal(); // ❌ cannot instantiate abstract class
        Dog dog = new Dog();
        dog.eat();    // inherited concrete method
        dog.sound();  // implemented abstract method
    }
}

```

✅ Output:

```Plain
Animal eats
Dog barks

```

---

### 🔹 Key Points

1. **Abstract classes** cannot be instantiated.
2. Can have **constructors**, **fields**, and **concrete methods**.
3. **Abstract methods** must be implemented in **non-abstract subclasses**.
4. Allows **partial implementation** of a class, providing **template behavior**.
5. Supports **polymorphism**: abstract class reference can hold subclass objects.

---

### 🔹 Using Abstract Class Reference

```Java
Animal a = new Dog(); // Polymorphism
a.eat();   // Animal eats
a.sound(); // Dog barks

```

- Reference type = abstract class
- Object type = concrete subclass
- Enables **dynamic dispatch**

---

### 🔹 Gotchas / Notes

- **Abstract class** can have **both abstract and concrete methods**.
- **Interfaces** can be used when full abstraction is needed (100% abstract).
- A class with **one or more abstract methods** must be **declared abstract**.

---

## 2. 📊 Summary Table

|Concept|Syntax / Example|Notes|
|---|---|---|
|Abstract class|`abstract class ClassName {}`|Cannot instantiate directly|
|Abstract method|`abstract void method();`|Must implement in subclass|
|Concrete method in abstract class|`void method() { ... }`|Can provide default behavior|
|Subclass|`class Sub extends AbstractClass { ... }`|Must implement all abstract methods|

---

### 🔹 Real-World Example

**Bank Accounts – Template with Abstract Class**

```Java
abstract class BankAccount {
    double balance;

    BankAccount(double balance) {
        this.balance = balance;
    }

    abstract void calculateInterest(); // abstract method

    void showBalance() { // concrete method
        System.out.println("Balance: " + balance);
    }
}

class SavingsAccount extends BankAccount {
    double interestRate = 0.05;

    SavingsAccount(double balance) {
        super(balance);
    }

    @Override
    void calculateInterest() {
        balance += balance * interestRate;
        System.out.println("Interest added: " + balance);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc = new SavingsAccount(1000); // abstract class reference
        acc.showBalance();          // Balance: 1000.0
        acc.calculateInterest();    // Interest added: 1050.0
    }
}

```

- Demonstrates **abstract class as template**, **abstract method implementation**, and **polymorphism**.