---
Created: 2025-09-16T19:46
tags:
  - Operators
---
# 🧩 Dart Arithmetic Operators Cheat Sheet

## 1. Full Explanation

### 🔹 Basic Arithmetic

- Dart supports standard arithmetic operators, very similar to C#, Java, and C++.

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`+`|Addition|`5 + 3`|`8`|
|`-`|Subtraction|`5 - 3`|`2`|
|`*`|Multiplication|`5 * 3`|`15`|
|`/`|Division (returns **double**)|`5 / 2`|`2.5`|
|`~/`|Integer Division (truncates)|`5 ~/ 2`|`2`|
|`%`|Modulus (remainder)|`5 % 2`|`1`|

---

### 🔹 Division vs Integer Division

- `/` always produces a **double**, even if dividing integers.
- `~/` truncates towards zero (like integer division in C/C#).

```Dart
print(7 / 2);   // 3.5 (double)
print(7 ~/ 2);  // 3   (int)
print(-7 ~/ 2); // -3  (towards zero)

```

---

### 🔹 Modulus `%`

- Returns the **remainder** after division.

```Dart
print(7 % 3);   // 1
print(-7 % 3);  // 2 (always keeps same sign as divisor in Dart)

```

---

### 🔹 Unary Operators

- Positive and negative signs can also act as unary operators.

```Dart
int x = 5;
print(-x); // -5
print(+x); // 5

```

---

### 🔹 Precedence Rules (highest → lowest relevant here)

1. , `/`, `~/`, `%`
2. `+`,

```Dart
print(2 + 3 * 4); // 14 (not 20)

```

---

## 2. Summary Table (Quick Reference)

|Operator|Name|Example|Result|
|---|---|---|---|
|`+`|Addition|`2 + 3`|`5`|
|`-`|Subtraction|`5 - 2`|`3`|
|`*`|Multiplication|`4 * 2`|`8`|
|`/`|Division (double)|`7 / 2`|`3.5`|
|`~/`|Integer Division|`7 ~/ 2`|`3`|
|`%`|Modulus|`7 % 2`|`1`|

---

## 3. Real-World Example

A **shopping cart calculation** with discounts:

```Dart
void main() {
  var pricePerItem = 120;
  var quantity = 7;

  var total = pricePerItem * quantity; // 840
  var discount = total ~/ 10;          // 10% discount, integer division
  var finalPrice = total - discount;

  print("Total: $total");
  print("Discount: $discount");
  print("Final Price: $finalPrice");

  // Split bill between 3 people
  var perPerson = finalPrice / 3;
  var perPersonRounded = finalPrice ~/ 3; // truncated
  var remainder = finalPrice % 3;         // leftover

  print("Per Person (exact): $perPerson");
  print("Per Person (rounded): $perPersonRounded");
  print("Remainder: $remainder");
}

```

**Output Example:**

```Plain
Total: 840
Discount: 84
Final Price: 756
Per Person (exact): 252.0
Per Person (rounded): 252
Remainder: 0

```

---

⚡ This example shows `*`, `-`, `/`, `~/`, and `%` in a practical context.