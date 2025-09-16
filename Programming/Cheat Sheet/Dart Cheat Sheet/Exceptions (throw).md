---
Created: 2025-09-16T20:10
tags:
  - Error-Handling
---
# 🎯 Dart Exception Handling Cheat Sheet

## 1. Full Explanation

- **Exceptions**: Errors that occur **during program execution**.
- Dart uses:
    - `try` → code that might throw an exception
    - `catch` → handles the exception
    - `finally` → optional block, runs regardless of exception
    - `throw` → raise an exception manually
- Helps **prevent program crashes** and implement **error recovery**.

---

## 2. Basic Example with `try` / `catch`

```Dart
void main() {
  try {
    int result = 12 ~/ 0; // integer division by zero
    print(result);
  } catch (e) {
    print("Caught an exception: $e");
  }
}

```

✅ Output: `Caught an exception: IntegerDivisionByZeroException`

---

## 3. Using `finally`

```Dart
void main() {
  try {
    print("Trying risky code...");
    throw FormatException("Invalid format");
  } catch (e) {
    print("Caught: $e");
  } finally {
    print("Finally block always runs");
  }
}

```

✅ `finally` executes **even if an exception occurs**.

---

## 4. Catching Specific Exceptions

```Dart
void main() {
  try {
    int.parse("abc"); // throws FormatException
  } on FormatException catch (e) {
    print("FormatException caught: $e");
  } on Exception catch (e) {
    print("Other exception: $e");
  } finally {
    print("Done handling exceptions");
  }
}

```

✅ Use `on Type catch (e)` to **catch specific exceptions**.

---

## 5. Throwing Custom Exceptions

```Dart
class InsufficientBalanceException implements Exception {
  String errMsg() => "Insufficient balance!";
}

void withdraw(double balance, double amount) {
  if (amount > balance) {
    throw InsufficientBalanceException();
  }
  print("Withdrawal successful");
}

void main() {
  try {
    withdraw(100, 200);
  } catch (e) {
    print(e); // Instance of 'InsufficientBalanceException'
  }
}

```

✅ You can create **custom exception classes** for better error handling.

---

## 6. Summary Table

|Keyword|Syntax|Notes|
|---|---|---|
|try|`try { ... }`|Code that may throw exception|
|catch|`catch (e)`|Handles any exception|
|on|`on ExceptionType catch (e)`|Handle specific exception types|
|finally|`finally { ... }`|Executes regardless of exception|
|throw|`throw Exception()`|Raises an exception manually|

---

## 7. Real-World Example

💡 **Bank Account Example**

```Dart
class InsufficientFundsException implements Exception {
  String message;
  InsufficientFundsException(this.message);
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
  } on InsufficientFundsException catch (e) {
    print("Error: ${e.message}");
  } finally {
    print("Transaction attempt finished");
  }
}

```

✅ Demonstrates **custom exception**, **throw**, **catch**, and **finally**.