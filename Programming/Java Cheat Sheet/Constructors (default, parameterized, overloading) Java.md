---
Created: 2025-08-25T19:47
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is a Constructor?

- A **constructor** is a **special method** used to **initialize objects**.
- **Has the same name as the class** and **no return type** (not even `void`).
- Called **automatically when an object is created**.

---

### 🔹 1. Default Constructor

- **No parameters**.
- Provided **implicitly** by Java if no constructor is defined.

```Java
public class Person {
    String name;
    int age;

    // Default constructor (explicit)
    public Person() {
        name = "Unknown";
        age = 0;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person p1 = new Person(); // calls default constructor
        p1.display(); // Name: Unknown, Age: 0
    }
}

```

---

### 🔹 2. Parameterized Constructor

- **Takes parameters** to initialize object fields with specific values.

```Java
public class Person {
    String name;
    int age;

    // Parameterized constructor
    public Person(String name, int age) {
        this.name = name; // 'this' refers to current object
        this.age = age;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person p2 = new Person("Alice", 25); // calls parameterized constructor
        p2.display(); // Name: Alice, Age: 25
    }
}

```

---

### 🔹 3. Constructor Overloading

- **Multiple constructors** with **different parameter lists** in the same class.

```Java
public class Person {
    String name;
    int age;

    // Default constructor
    public Person() {
        name = "Unknown";
        age = 0;
    }

    // Parameterized constructor
    public Person(String name) {
        this.name = name;
        age = 0;
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person p1 = new Person();
        Person p2 = new Person("Bob");
        Person p3 = new Person("Charlie", 30);

        p1.display(); // Name: Unknown, Age: 0
        p2.display(); // Name: Bob, Age: 0
        p3.display(); // Name: Charlie, Age: 30
    }
}

```

- Allows **flexibility** in object creation.

---

### 🔹 Gotchas / Notes

- If you define **any constructor**, Java **does not provide a default constructor automatically**.
- Use `this` keyword to refer to **current object**.
- Constructor **overloading** is similar to **method overloading**.
- Constructors **cannot have a return type**, not even `void`.

---

## 2. 📊 Summary Table

|Constructor Type|Syntax / Example|Notes|
|---|---|---|
|Default|`ClassName(){}`|No parameters, auto-provided if none defined|
|Parameterized|`ClassName(params){}`|Initialize object fields with values|
|Overloaded|Multiple constructors with different params|Provides flexibility in creating objects|
|`this` keyword|`this.field = param;`|Refers to current object|

---

### 🔹 Real-World Example

**Bank Account Class with Constructor Overloading**

```Java
public class BankAccount {
    String accountHolder;
    double balance;

    // Default constructor
    public BankAccount() {
        accountHolder = "Unknown";
        balance = 0;
    }

    // Parameterized constructor
    public BankAccount(String accountHolder) {
        this.accountHolder = accountHolder;
        balance = 0;
    }

    // Parameterized constructor with balance
    public BankAccount(String accountHolder, double balance) {
        this.accountHolder = accountHolder;
        this.balance = balance;
    }

    public void display() {
        System.out.println(accountHolder + "'s balance: " + balance);
    }

    public static void main(String[] args) {
        BankAccount a1 = new BankAccount();
        BankAccount a2 = new BankAccount("Alice");
        BankAccount a3 = new BankAccount("Bob", 1000);

        a1.display(); // Unknown's balance: 0.0
        a2.display(); // Alice's balance: 0.0
        a3.display(); // Bob's balance: 1000.0
    }
}

```

- Demonstrates **default constructor**, **parameterized constructors**, and **overloading** in one class.