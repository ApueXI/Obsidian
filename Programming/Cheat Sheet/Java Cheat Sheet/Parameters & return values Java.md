---
Created: 2025-08-25T19:35
tags:
  - Methods-(Funciton)
---
## 1. Full Explanation

### 🔹 What Are Parameters?

- **Parameters** are inputs a method can accept to perform operations.
- Two types:
    1. **Primitive parameters** → pass **copy of value** (call by value).
    2. **Reference parameters** → pass **reference to object** (changes affect original object).

### 🔹 Syntax

```Java
modifier returnType methodName(type param1, type param2, ...) {
    // method body
}

```

**Example:**

```Java
public int add(int a, int b) {
    return a + b;
}

```

---

### 🔹 Calling a Method with Arguments

```Java
int result = add(5, 10); // 5 → a, 10 → b
System.out.println(result); // 15

```

---

### 🔹 Return Values

- The **value a method returns** to the caller.
- Syntax: `return value;`
- Must **match the declared return type**.
- Use `void` if **no value is returned**.

```Java
public int multiply(int x, int y) {
    return x * y; // returns int
}

public void greet(String name) {
    System.out.println("Hello " + name); // no return value
}

```

---

### 🔹 Return Type Examples

|Return Type|Example|Notes|
|---|---|---|
|Primitive|`int add(int a, int b)`|Returns a single primitive value|
|Object / Reference|`String getName()`|Returns a reference to an object|
|void|`void printHello()`|No value returned, just performs action|

---

### 🔹 Gotchas

- Returning **different type** than declared → compile-time error.
- Multiple `return` statements allowed, but **only one executes per call**.
- Primitive parameters → changes **do not affect original** value.
- Reference parameters → object **can be modified** inside method.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Parameters|`(type name, ...)`|Inputs to method|
|Arguments|`method(arg1, arg2)`|Values passed to parameters|
|Return Value|`return value;`|Must match declared return type|
|void|`void method()`|No value returned|
|Call by Value|Primitive types|Changes do not affect original|
|Call by Reference|Objects|Changes affect original object|

---

## 3. 🌍 Real-World Example

### ✅ Banking System: Deposit & Withdraw

```Java
public class BankAccount {
    private double balance;

    public BankAccount(double initial) {
        balance = initial;
    }

    public void deposit(double amount) { // void, no return
        balance += amount;
        System.out.println("Deposited: " + amount);
    }

    public boolean withdraw(double amount) { // returns boolean
        if (amount > balance) {
            System.out.println("Insufficient funds!");
            return false;
        } else {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
            return true;
        }
    }

    public double getBalance() { // returns double
        return balance;
    }

    public static void main(String[] args) {
        BankAccount myAcc = new BankAccount(1000);

        myAcc.deposit(500);           // void
        boolean success = myAcc.withdraw(200); // returns true
        System.out.println("Transaction success? " + success);

        double curr = myAcc.getBalance(); // returns balance
        System.out.println("Current Balance: " + curr);
    }
}

```

✅ Output:

```Plain
Deposited: 500.0
Withdrew: 200.0
Transaction success? true
Current Balance: 1300.0

```

- Shows **parameters** (`amount`) and **return values** (`boolean` for withdraw, `double` for getBalance).