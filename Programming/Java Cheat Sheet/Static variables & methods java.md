---
Created: 2025-08-25T20:00
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is `static`?

- The `**static**` **keyword** is used to define **class-level members** (variables or methods) rather than **instance-level**.
- **Static members** are **shared across all objects** of the class.
- Accessed via **class name** rather than object reference.

---

### 🔹 Static Variables (Class Variables)

- **Shared across all objects** of the class.
- Declared using `static`.

```Java
class Counter {
    static int count = 0; // static variable

    Counter() {
        count++; // increment for every object created
    }

    static void displayCount() {
        System.out.println("Count: " + count);
    }
}

public class Main {
    public static void main(String[] args) {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        Counter c3 = new Counter();

        Counter.displayCount(); // Count: 3
    }
}

```

- All instances share the **same** `**count**` **value**.
- Access via `**ClassName.variable**`, not via object reference (although allowed, not recommended).

---

### 🔹 Static Methods (Class Methods)

- Belong to the **class**, not the object.
- Can **access only static variables or call other static methods** directly.
- Cannot use `**this**` inside a static method.

```Java
class MathUtil {
    static double pi = 3.14159; // static variable

    static double areaOfCircle(double radius) { // static method
        return pi * radius * radius;
    }
}

public class Main {
    public static void main(String[] args) {
        double area = MathUtil.areaOfCircle(5);
        System.out.println("Area: " + area); // Area: 78.53975
    }
}

```

- Called via `**ClassName.method()**`.

---

### 🔹 Key Points

1. **Static variable** → shared across all objects.
2. **Static method** → cannot access instance variables/methods directly.
3. Can be accessed **without creating an object**.
4. Can be used for **utility or helper methods**.
5. Static **blocks** can initialize static variables at class loading.

---

### 🔹 Gotchas / Notes

- Avoid overusing static → reduces **object-oriented flexibility**.
- Static methods **cannot be overridden**, they can only be **hidden**.
- Static methods **cannot use** `**super**` **or** `**this**`.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Static variable|`static int count;`|Shared across all objects|
|Static method|`static void method(){}`|Belongs to class, no `this`|
|Access|`ClassName.variable` / `ClassName.method()`|Preferred way|
|Static block|`static { ... }`|Initialize static variables|

---

### 🔹 Real-World Example

**Bank System – Static Variable**

```Java
class BankAccount {
    private static int accountCounter = 0; // shared across all accounts
    private int accountNumber;
    private double balance;

    BankAccount(double balance) {
        accountCounter++;
        this.accountNumber = accountCounter; // unique account number
        this.balance = balance;
    }

    public static int getAccountCounter() {
        return accountCounter;
    }

    public void showAccount() {
        System.out.println("Account #" + accountNumber + ", Balance: " + balance);
    }

    public static void main(String[] args) {
        BankAccount a1 = new BankAccount(1000);
        BankAccount a2 = new BankAccount(2000);
        BankAccount a3 = new BankAccount(3000);

        a1.showAccount(); // Account #1, Balance: 1000.0
        a2.showAccount(); // Account #2, Balance: 2000.0
        a3.showAccount(); // Account #3, Balance: 3000.0

        System.out.println("Total accounts: " + BankAccount.getAccountCounter()); // 3
    }
}

```

- Demonstrates **static variable for shared counter** and **static method to access it**.