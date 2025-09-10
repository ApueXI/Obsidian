---
Created: 2025-08-25T19:49
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What Are Access Modifiers?

- **Access modifiers** control the **visibility** of **classes, fields, methods, and constructors**.
- They define **which parts of a program can access a particular member**.

---

### 🔹 Types of Access Modifiers

|Modifier|Applies To|Visibility / Scope|
|---|---|---|
|**public**|Class, Field, Method, Constructor|Accessible from **anywhere** (any class, package)|
|**private**|Field, Method, Constructor|Accessible **only within the same class**|
|**protected**|Field, Method, Constructor|Accessible in **same package** and **subclasses** (even in other packages)|
|default (no modifier)|Class, Field, Method, Constructor|Accessible **only within the same package**|

---

### 🔹 Examples

```Java
// File: Person.java
package mypackage;

public class Person {      // public class
    public String name;    // public field
    private int age;       // private field
    protected String email;// protected field
    String address;        // default field (no modifier)

    // public method
    public void greet() {
        System.out.println("Hello, my name is " + name);
    }

    // private method
    private void showAge() {
        System.out.println("Age: " + age);
    }

    // protected method
    protected void showEmail() {
        System.out.println("Email: " + email);
    }

    // default method
    void showAddress() {
        System.out.println("Address: " + address);
    }
}

```

---

### 🔹 Access from Another Class

```Java
package mypackage;

public class Main {
    public static void main(String[] args) {
        Person p = new Person();
        p.name = "Alice";       // ✅ public
        // p.age = 25;          // ❌ private
        p.email = "a@abc.com";  // ✅ protected (same package)
        p.address = "Street 1"; // ✅ default (same package)

        p.greet();              // ✅ public
        // p.showAge();         // ❌ private
        p.showEmail();          // ✅ protected
        p.showAddress();        // ✅ default
    }
}

```

- **Private** → only accessible inside `Person` class
- **Default** → accessible within same package
- **Protected** → accessible in same package + subclasses
- **Public** → accessible anywhere

---

### 🔹 Gotchas / Notes

- **Top-level classes** can only be **public** or **default**; cannot be private or protected.
- **Private members** are commonly used with **encapsulation (getters & setters)**.
- **Protected** is mainly used for **inheritance**.
- **Default (package-private)** is useful to hide details from outside the package.

---

## 2. 📊 Summary Table

|Modifier|Scope / Visibility|Example Use|
|---|---|---|
|public|Anywhere|API methods, main classes|
|private|Class only|Fields, helper methods|
|protected|Same package + subclasses|Inherited fields/methods|
|default|Same package|Package-internal access, hide from other packages|

---

### 🔹 Real-World Example

**Bank Account Access Modifiers**

```Java
public class BankAccount {
    private String accountNumber;  // only class can access
    private double balance;
    public String accountHolder;   // accessible anywhere

    protected void deposit(double amount) { // accessible in subclass or package
        balance += amount;
    }

    void showBalance() { // default, package access
        System.out.println("Balance: " + balance);
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        acc.accountHolder = "Alice"; // public
        // acc.balance = 1000;       // ❌ private
        acc.showBalance();           // default
        acc.deposit(500);            // protected
    }
}

```

✅ Demonstrates **control of access** using modifiers.