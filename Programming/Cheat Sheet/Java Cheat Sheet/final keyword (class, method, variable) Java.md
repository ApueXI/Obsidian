---
Created: 2025-08-25T20:03
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is `final`?

- The `**final**` **keyword** in Java is used to **restrict or lock something**, meaning it **cannot be changed or overridden**.
- Can be applied to:
    1. **Variables** → value cannot change
    2. **Methods** → cannot be overridden
    3. **Classes** → cannot be subclassed

---

### 🔹 1. Final Variable

- A **variable marked final** becomes a **constant**.
- Must be **initialized at declaration** or in **constructor (for instance variables)**.

```Java
class Example {
    final int MAX = 100; // initialized at declaration

    final int MIN;       // initialized in constructor

    Example() {
        MIN = 0; // OK
    }

    void print() {
        System.out.println("MAX: " + MAX + ", MIN: " + MIN);
    }

    public static void main(String[] args) {
        Example e = new Example();
        e.print(); // MAX: 100, MIN: 0
        // e.MAX = 200; // ❌ Cannot assign a value to final variable
    }
}

```

- **Local final variables** inside methods behave the same.
- **Static final variables** → constants shared by all objects.

```Java
class Constants {
    static final double PI = 3.14159;
}

```

---

### 🔹 2. Final Method

- A **final method cannot be overridden** by subclasses.
- Useful to **preserve behavior** in inheritance.

```Java
class Animal {
    final void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    // void eat() { System.out.println("Dog eats"); } // ❌ Cannot override final method
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat(); // Animal eats
    }
}

```

---

### 🔹 3. Final Class

- A **final class cannot be subclassed**.
- Useful to **prevent inheritance**, e.g., `String` class.

```Java
final class Utility {
    static void printHello() {
        System.out.println("Hello!");
    }
}

// class ExtendedUtility extends Utility {} // ❌ Cannot inherit final class

public class Main {
    public static void main(String[] args) {
        Utility.printHello(); // Hello!
    }
}

```

---

### 🔹 Key Points

1. **Final variable** → constant, cannot be reassigned.
2. **Final method** → cannot be overridden.
3. **Final class** → cannot be subclassed.
4. **Blank final variable** → can be assigned **once in constructor**.
5. Final + static → **compile-time constants**.

---

### 🔹 Gotchas / Notes

- **Final objects** → reference cannot change, but **object content can change** (mutable objects).

```Java
final int[] arr = {1, 2, 3};
arr[0] = 10; // ✅ Allowed
// arr = new int[5]; // ❌ Not allowed

```

- **Final parameters** → parameter cannot be reassigned inside method.

```Java
void print(final int x) {
    // x = 5; // ❌ Not allowed
}

```

---

## 2. 📊 Summary Table

|Type|Syntax / Example|Notes|
|---|---|---|
|Final Variable|`final int x = 10;`|Value cannot change|
|Final Method|`final void method(){}`|Cannot be overridden|
|Final Class|`final class ClassName {}`|Cannot be subclassed|
|Final Object|`final Object obj = new Object();`|Reference cannot change, object content can|
|Final Parameter|`void method(final int x)`|Parameter cannot be reassigned|

---

### 🔹 Real-World Example

**Bank Account Constants**

```Java
class BankAccount {
    private static final double MIN_BALANCE = 1000; // constant

    private double balance;

    BankAccount(double balance) {
        if(balance >= MIN_BALANCE) {
            this.balance = balance;
        } else {
            this.balance = MIN_BALANCE;
        }
    }

    final void showBalance() { // cannot be overridden
        System.out.println("Balance: " + balance);
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount(500);
        acc.showBalance(); // Balance: 1000.0
    }
}

```

- Demonstrates **final variable**, **final method**, and **static final constant**.