---
Created: 2025-08-25T19:35
tags:
  - Methods-(Funciton)
---
## 1. Full Explanation

### 🔹 What is a Method?

- A **method** is a **block of code** that performs a specific task.
- Helps **reusability**, **modularity**, and **readability**.

---

### 🔹 Method Declaration

Syntax:

```Java
modifier returnType methodName(parameterList) {
    // method body
}

```

- **modifier** → access specifier (`public`, `private`, `protected`, or default).
- **returnType** → type of value returned (`void` if none).
- **methodName** → descriptive name of method.
- **parameterList** → inputs (can be empty).

**Example:**

```Java
public int add(int a, int b) {
    return a + b;
}

public void greet(String name) {
    System.out.println("Hello, " + name + "!");
}

```

---

### 🔹 Method Calling

- Call a method **by name** and pass **arguments** if needed.
- Example:

```Java
public class Main {
    public static void main(String[] args) {
        Main obj = new Main();        // create object for non-static methods

        int sum = obj.add(5, 10);     // call add
        System.out.println("Sum: " + sum);

        obj.greet("Alice");            // call greet
    }

    public int add(int a, int b) {
        return a + b;
    }

    public void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }
}

```

✅ Output:

```Plain
Sum: 15
Hello, Alice!

```

---

### 🔹 Static vs Non-Static Methods

|Type|How to Call|Example|
|---|---|---|
|Static|Using class name or directly in `static main`|`Math.max(5,10)`|
|Non-static|Using object of class|`obj.greet("Alice")`|

**Static Example:**

```Java
public class Utils {
    public static int square(int n) {
        return n * n;
    }

    public static void main(String[] args) {
        int result = Utils.square(5); // no object needed
        System.out.println(result);
    }
}

```

---

### 🔹 Gotchas

- Calling **non-static methods** from a **static context** requires an object.
- Methods can be **overloaded** → same name, different parameters.
- `return` ends method execution and optionally returns a value.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Declaration|`modifier returnType name(params){}`|Create reusable code block|
|Call|`object.method(args)` or `Class.method(args)` (static)|Execute method|
|Return type|`void` or any type|Use `return value;` for non-void|
|Static vs Non-static|`static` → call via class, non-static → call via object|Only static accessible in static context directly|
|Parameters|Any number, any type|Can be primitive or reference|
|Overloading|Same name, different param types|Helps flexibility|

---

### 🔹 Real-World Example

Imagine a **Bank Account System**:

```Java
public class BankAccount {
    private double balance;

    public BankAccount(double initial) {
        balance = initial;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited: " + amount);
    }

    public void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient funds!");
        } else {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        }
    }

    public double getBalance() {
        return balance;
    }

    public static void main(String[] args) {
        BankAccount myAcc = new BankAccount(1000);
        myAcc.deposit(500);
        myAcc.withdraw(200);
        System.out.println("Current Balance: " + myAcc.getBalance());
    }
}

```

✅ Output:

```Plain
Deposited: 500.0
Withdrew: 200.0
Current Balance: 1300.0

```

- Demonstrates **declaring**, **calling**, and **using return values** from methods.