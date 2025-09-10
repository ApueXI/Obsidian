---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

**Encapsulation** is one of the four pillars of Object-Oriented Programming (OOP). It means **hiding the internal state (data) of an object** and **restricting direct access** to some of its components.

- This protects the **integrity of the data**.
- Access is controlled through **public methods or properties**.

---

## 🧠 How Encapsulation Works in C#

- Make **fields private** to hide them.
- Use **properties** with getters and setters to control access.
- Validate data inside setters to prevent invalid states.
- Limit exposure of sensitive data or functionality.

---

## 🧩 Example

```C#
public class BankAccount
{
    private decimal balance;  // Private field

    public decimal Balance    // Public property controls access
    {
        get { return balance; }
        private set          // Only settable within class
        {
            if (value < 0)
                throw new ArgumentException("Balance cannot be negative");
            balance = value;
        }
    }

    public BankAccount(decimal initialBalance)
    {
        Balance = initialBalance;  // Uses property setter (with validation)
    }

    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Deposit must be positive");
        Balance += amount;
    }

    public void Withdraw(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Withdrawal must be positive");
        if (amount > Balance)
            throw new InvalidOperationException("Insufficient funds");
        Balance -= amount;
    }
}
```

---

## 🔄 Benefits of Encapsulation

|Benefit|Explanation|
|---|---|
|Data protection|Prevents invalid or inconsistent data states|
|Hides complexity|Internal details are hidden from users|
|Easier maintenance|Changes inside class don’t affect external code|
|Controlled access|Read-only or write-only access via properties|
|Increases modularity|Components communicate through defined interfaces|

---

## 📋 Best Practices

- Always **keep fields private**.
- Expose data through **properties**.
- Use **validation** inside property setters or methods.
- Keep class **interfaces clean and minimal**.
- Avoid exposing internal objects directly; provide copies or read-only views.
- Use **immutable classes** where possible for thread safety.

---

## 🧠 Quick Reference

|Encapsulation Aspect|How to Implement|
|---|---|
|Hide data|`private` fields|
|Controlled access|Public **properties** with `get`/`set`|
|Validation|Logic inside setters or methods|
|Read-only access|Property with only `get` accessor|
|Write-only access|Property with only `set` accessor|