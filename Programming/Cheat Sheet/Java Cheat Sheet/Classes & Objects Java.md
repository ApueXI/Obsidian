---
Created: 2025-08-25T19:44
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is a Class?

- A **class** is a **blueprint** for creating objects.
- Defines **fields (variables)** and **methods** that objects will have.

### 🔹 What is an Object?

- An **object** is an **instance of a class**.
- Contains **actual values** for the fields defined in the class.

---

### 🔹 Syntax: Declaring a Class

```Java
public class Person {
    // Fields (properties)
    String name;
    int age;

    // Method
    public void greet() {
        System.out.println("Hello, my name is " + name);
    }
}

```

---

### 🔹 Creating & Using Objects

```Java
public class Main {
    public static void main(String[] args) {
        // Create an object
        Person person1 = new Person();

        // Assign values to fields
        person1.name = "Alice";
        person1.age = 25;

        // Call method
        person1.greet(); // Output: Hello, my name is Alice
        System.out.println("Age: " + person1.age); // Output: Age: 25
    }
}

```

---

### 🔹 Key Points

- **Fields** → store object data (variables).
- **Methods** → define behavior of objects.
- **Accessing members** → `object.field` or `object.method()`.
- **Objects occupy memory**, while **classes do not** (class is just blueprint).

---

### 🔹 Constructor (Optional Intro)

- A **constructor** initializes objects.
- Has **same name as class** and **no return type**.

```Java
public class Person {
    String name;
    int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void greet() {
        System.out.println("Hello, my name is " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Person person2 = new Person("Bob", 30);
        person2.greet(); // Hello, my name is Bob
    }
}

```

---

### 🔹 Gotchas / Notes

- **Every object has its own copy** of instance variables.
- **Methods are shared**, unless `static`.
- Objects are **accessed via references**, not the actual value directly.
- Classes can be **public, default, abstract, or final**.

---

## 2. 📊 Summary Table

|Concept|Syntax / Example|Notes|
|---|---|---|
|Class|`class ClassName { ... }`|Blueprint for objects|
|Object|`ClassName obj = new ClassName();`|Instance of a class|
|Field|`object.field`|Stores object data|
|Method|`object.method()`|Defines object behavior|
|Constructor|`ClassName(params){...}`|Initializes object|

---

### 🔹 Real-World Example

**Bank Account Class**

```Java
public class BankAccount {
    String accountHolder;
    double balance;

    // Constructor
    public BankAccount(String accountHolder, double balance) {
        this.accountHolder = accountHolder;
        this.balance = balance;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited: " + amount);
    }

    public void withdraw(double amount) {
        if(amount > balance) {
            System.out.println("Insufficient funds!");
        } else {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        }
    }

    public void displayBalance() {
        System.out.println(accountHolder + "'s balance: " + balance);
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount("Alice", 1000);
        acc.deposit(500);
        acc.withdraw(200);
        acc.displayBalance();
    }
}

```

✅ Output:

```Plain
Deposited: 500.0
Withdrew: 200.0
Alice's balance: 1300.0

```

- Shows **creating class**, **object**, **fields**, **methods**, and **constructor**.