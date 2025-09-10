---
Created: 2025-08-25T19:48
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is `this`?

- `this` is a **reference variable** that **refers to the current object** of the class.
- Commonly used to **differentiate between instance variables and parameters**, **call other constructors**, and **pass current object**.

---

### 🔹 1. Distinguishing Instance Variables from Parameters

```Java
public class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name; // 'this.name' refers to the field, 'name' refers to parameter
        this.age = age;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person p = new Person("Alice", 25);
        p.display(); // Name: Alice, Age: 25
    }
}

```

- Without `this`, assigning `name = name;` would **do nothing**, as parameter shadows the field.

---

### 🔹 2. Calling Another Constructor (`this()`)

- You can **call one constructor from another** to avoid code duplication.
- Must be the **first statement** in the constructor.

```Java
public class Person {
    String name;
    int age;

    // Default constructor
    public Person() {
        this("Unknown", 0); // call parameterized constructor
    }

    // Parameterized constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person p1 = new Person();
        Person p2 = new Person("Bob", 30);

        p1.display(); // Name: Unknown, Age: 0
        p2.display(); // Name: Bob, Age: 30
    }
}

```

---

### 🔹 3. Passing Current Object as Argument

```Java
public class Car {
    String model;

    public Car(String model) {
        this.model = model;
    }

    public void print(Car obj) {
        System.out.println("Car model: " + obj.model);
    }

    public void show() {
        print(this); // pass current object
    }

    public static void main(String[] args) {
        Car c = new Car("Toyota");
        c.show(); // Car model: Toyota
    }
}

```

---

### 🔹 4. Returning Current Object

- Useful for **method chaining**.

```Java
public class Person {
    String name;
    int age;

    public Person setName(String name) {
        this.name = name;
        return this;
    }

    public Person setAge(int age) {
        this.age = age;
        return this;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person p = new Person();
        p.setName("Alice").setAge(25).display(); // Name: Alice, Age: 25
    }
}

```

---

### 🔹 Gotchas / Notes

- `this` **cannot be used in static methods** → no current object exists.
- `this()` call must be **first statement** in constructor.
- Improves **code readability** and **avoids shadowing issues**.

---

## 2. 📊 Summary Table

|Use Case|Syntax / Example|Notes|
|---|---|---|
|Access instance variables|`this.field`|Differentiate from parameters|
|Call another constructor|`this(params)`|Must be first line|
|Pass current object|`method(this)`|Pass object reference to another method|
|Return current object|`return this;`|Enable method chaining|

---

### 🔹 Real-World Example

**Bank Account with Method Chaining**

```Java
public class BankAccount {
    String accountHolder;
    double balance;

    public BankAccount setAccountHolder(String accountHolder) {
        this.accountHolder = accountHolder;
        return this;
    }

    public BankAccount setBalance(double balance) {
        this.balance = balance;
        return this;
    }

    public void display() {
        System.out.println(accountHolder + "'s balance: " + balance);
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        acc.setAccountHolder("Alice")
           .setBalance(1000)
           .display(); // Alice's balance: 1000.0
    }
}

```

- Demonstrates **using** `**this**` **to access fields**, **return object**, and **method chaining**.