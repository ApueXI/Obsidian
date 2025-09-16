---
Created: 2025-09-16T20:12
tags:
  - Error-Handling
---
# 🎯 Dart Custom Exceptions Cheat Sheet

## 1. Full Explanation

- Dart allows you to **create your own exceptions** by **extending** `**Exception**` (or `Error`).
- Custom exceptions make your code **more descriptive and maintainable**.
- Typically, you define:
    - **Fields** (optional, e.g., message, code)
    - **Constructor**
    - `**toString()**` for human-readable output

---

## 2. Basic Custom Exception

```Dart
class InsufficientBalanceException implements Exception {
  String message;
  InsufficientBalanceException(this.message);

  @override
  String toString() => "InsufficientBalanceException: $message";
}

void main() {
  try {
    throw InsufficientBalanceException("Balance too low!");
  } catch (e) {
    print(e); // InsufficientBalanceException: Balance too low!
  }
}

```

✅ `implements Exception` (or `extends Exception`) signals this is an exception type.

---

## 3. Using Custom Exception in a Function

```Dart
class NegativeValueException implements Exception {
  String message;
  NegativeValueException(this.message);

  @override
  String toString() => "NegativeValueException: $message";
}

double squareRoot(double value) {
  if (value < 0) throw NegativeValueException("Cannot take square root of negative number");
  return value.sqrt(); // pretend sqrt() exists
}

void main() {
  try {
    squareRoot(-9);
  } catch (e) {
    print(e); // NegativeValueException: Cannot take square root of negative number
  }
}

```

✅ Custom exceptions make **domain-specific errors explicit**.

---

## 4. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Define custom exception|`class MyException implements Exception { ... }`|Can include fields and methods|
|Throw custom exception|`throw MyException("message");`|Raises the exception|
|Catch exception|`try { ... } catch (e)`|Handle it like normal exceptions|
|Override `toString()`|`@override String toString() => ...`|Makes error messages human-readable|

---

## 5. Real-World Example

💡 **Bank Account Example**

```Dart
class InsufficientFundsException implements Exception {
  String message;
  InsufficientFundsException(this.message);

  @override
  String toString() => "InsufficientFundsException: $message";
}

class BankAccount {
  double balance;
  BankAccount(this.balance);

  void withdraw(double amount) {
    if (amount > balance) {
      throw InsufficientFundsException("Cannot withdraw \$${amount}, balance is \$${balance}");
    }
    balance -= amount;
    print("Withdrawal successful. Remaining balance: \$${balance}");
  }
}

void main() {
  var account = BankAccount(100);

  try {
    account.withdraw(200);
  } catch (e) {
    print(e); // InsufficientFundsException: Cannot withdraw $200, balance is $100
  }
}

```

✅ Custom exceptions make your code **self-documenting** and **easier to debug**.