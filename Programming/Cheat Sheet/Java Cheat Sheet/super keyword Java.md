---
Created: 2025-08-25T19:57
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is `super`?

- `super` is a **reference variable** used in a **subclass** to refer to its **immediate parent class**.
- Useful to:
    1. Call **parent class methods**
    2. Access **parent class fields**
    3. Call **parent class constructors**

---

### 🔹 1. Accessing Parent Class Fields

```Java
class Animal {
    String color = "White";
}

class Dog extends Animal {
    String color = "Brown";

    void printColor() {
        System.out.println("Dog color: " + color);       // Child field
        System.out.println("Animal color: " + super.color); // Parent field
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.printColor();
    }
}

```

✅ Output:

```Plain
Dog color: Brown
Animal color: White

```

- `**super.color**` refers to **parent class field**.

---

### 🔹 2. Calling Parent Class Methods

```Java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    @Override
    void eat() {
        super.eat(); // call parent method
        System.out.println("Dog eats bones");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();
    }
}

```

✅ Output:

```Plain
Animal eats
Dog eats bones

```

- `**super.eat()**` calls the **method from parent class**.

---

### 🔹 3. Calling Parent Class Constructor

- Can call a **parent class constructor** from child using `super()`.
- Must be the **first statement** in the child constructor.

```Java
class Animal {
    Animal() {
        System.out.println("Animal constructor called");
    }
}

class Dog extends Animal {
    Dog() {
        super(); // call parent constructor
        System.out.println("Dog constructor called");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
    }
}

```

✅ Output:

```Plain
Animal constructor called
Dog constructor called

```

- Avoids **duplicating initialization code**.

---

### 🔹 Gotchas / Notes

- `super` cannot be used in **static methods** → no current object exists.
- `super()` call **must be first statement** in child constructor.
- Can be used to **access hidden fields** or **override methods** from parent.

---

## 2. 📊 Summary Table

|Use Case|Syntax / Example|Notes|
|---|---|---|
|Access parent field|`super.field`|Access hidden field in parent|
|Call parent method|`super.method()`|Access overridden method|
|Call parent constructor|`super()`|Must be first statement in constructor|

---

### 🔹 Real-World Example

**Bank Accounts**

```Java
class BankAccount {
    double balance;

    BankAccount(double balance) {
        this.balance = balance;
        System.out.println("BankAccount created with balance: " + balance);
    }

    void showBalance() {
        System.out.println("Balance: " + balance);
    }
}

class SavingsAccount extends BankAccount {
    double interestRate;

    SavingsAccount(double balance, double interestRate) {
        super(balance); // call parent constructor
        this.interestRate = interestRate;
    }

    @Override
    void showBalance() {
        super.showBalance(); // call parent method
        System.out.println("Interest rate: " + interestRate);
    }

    public static void main(String[] args) {
        SavingsAccount sa = new SavingsAccount(1000, 0.05);
        sa.showBalance();
    }
}

```

✅ Output:

```Plain
BankAccount created with balance: 1000.0
Balance: 1000.0
Interest rate: 0.05

```

- Demonstrates **super() constructor call**, **super method**, and **field access**.