---
Created: 2025-08-25T19:48
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is Encapsulation?

- **Encapsulation** = wrapping **fields (data)** and **methods (behavior)** into a **single class**.
- Provides **data hiding** by making fields `private` and controlling access via **getters and setters**.
- Improves **security**, **modularity**, and **maintainability**.

---

### 🔹 Getters & Setters

|Type|Purpose|Syntax|
|---|---|---|
|Getter|Retrieve value of a private field|`public type getField() { return field; }`|
|Setter|Update value of a private field|`public void setField(type value) { this.field = value; }`|

---

### 🔹 Example: Person Class

```Java
public class Person {
    // Private fields
    private String name;
    private int age;

    // Getter for name
    public String getName() {
        return name;
    }

    // Setter for name
    public void setName(String name) {
        this.name = name;
    }

    // Getter for age
    public int getAge() {
        return age;
    }

    // Setter for age
    public void setAge(int age) {
        if(age > 0) { // validation
            this.age = age;
        }
    }

    public static void main(String[] args) {
        Person p = new Person();
        p.setName("Alice");
        p.setAge(25);

        System.out.println("Name: " + p.getName()); // Alice
        System.out.println("Age: " + p.getAge());   // 25
    }
}

```

- **Private fields** → cannot be accessed directly outside the class.
- **Getters & setters** → controlled access with optional validation.

---

### 🔹 Key Points

- **Always make fields private** to hide data.
- **Use getters** to read values.
- **Use setters** to modify values safely.
- Can include **validation logic** inside setters.
- Supports **immutability** if you provide only getters (no setters).

---

### 🔹 Gotchas / Notes

- Overuse of setters can expose too much internal state → balance encapsulation.
- Naming convention:
    - Getter: `getField()`
    - Setter: `setField(value)`
- Boolean fields can have getter `isField()`

```Java
private boolean active;
public boolean isActive() { return active; }
public void setActive(boolean active) { this.active = active; }

```

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Private field|`private int age;`|Hidden from outside class|
|Getter|`public int getAge() { return age; }`|Access value safely|
|Setter|`public void setAge(int age) { this.age = age; }`|Modify value safely, can include validation|
|Boolean getter|`isActive()`|Common for boolean fields|

---

### 🔹 Real-World Example

**Bank Account Encapsulation**

```Java
public class BankAccount {
    private String accountHolder;
    private double balance;

    public String getAccountHolder() {
        return accountHolder;
    }

    public void setAccountHolder(String accountHolder) {
        this.accountHolder = accountHolder;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if(amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if(amount > 0 && amount <= balance) {
            balance -= amount;
        } else {
            System.out.println("Insufficient funds or invalid amount");
        }
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        acc.setAccountHolder("Alice");
        acc.deposit(1000);
        acc.withdraw(500);

        System.out.println(acc.getAccountHolder() + "'s balance: " + acc.getBalance());
    }
}

```

✅ Output:

```Plain
Alice's balance: 500.0

```

- Fields are **private**, accessed and modified **only through methods**, ensuring **data security**.