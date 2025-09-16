---
Created: 2025-09-16T19:49
tags:
  - Operators
---
# 🧩 Dart Assignment Operators Cheat Sheet

## 1. Full Explanation

Assignment operators are used to **store values into variables** or **update variables**.

### 🔹 Basic Assignment `=`

- Assigns a value to a variable.

```Dart
var x = 10;   // assigns 10

```

---

### 🔹 Compound Assignment (`+=`, `=`, `=`, `/=`, `~/=`, `%=`, `&=`, `|=`, `^=`, `<<=`, `>>=`, `>>>=`)

- Combines an operation with assignment.

```Dart
var a = 5;
a += 3;   // a = a + 3 → 8
a -= 2;   // a = a - 2 → 6
a *= 4;   // a = a * 4 → 24
a ~/= 5;  // a = a ~/ 5 → 4 (integer division)
a %= 3;   // a = a % 3 → 1

```

---

### 🔹 Null-Aware Assignment (`??=`)

- Assigns value **only if the variable is null**.

```Dart
int? b;
b ??= 10; // b = 10 (since it was null)
b ??= 20; // no change, stays 10

```

---

### 🔹 With Bitwise Operators

- Dart also supports assignment with bitwise operators:

```Dart
var c = 5;     // 0101 in binary
c &= 3;        // c = 5 & 3 → 1
c |= 8;        // c = 1 | 8 → 9
c ^= 2;        // c = 9 ^ 2 → 11
c <<= 1;       // c = 11 << 1 → 22
c >>= 2;       // c = 22 >> 2 → 5

```

---

### 🔹 Chained Assignment

- You can assign multiple variables at once.

```Dart
var x, y, z;
x = y = z = 100;
print(x); // 100
print(y); // 100
print(z); // 100

```

---

## 2. Summary Table (Quick Reference)

|Operator|Meaning|Example|Equivalent|
|---|---|---|---|
|`=`|Assign|`x = 5`|—|
|`+=`|Add & assign|`x += 2`|`x = x + 2`|
|`-=`|Subtract & assign|`x -= 2`|`x = x - 2`|
|`*=`|Multiply & assign|`x *= 3`|`x = x * 3`|
|`/=`|Divide & assign|`x /= 2`|`x = x / 2`|
|`~/=`|Integer divide & assign|`x ~/= 2`|`x = x ~/ 2`|
|`%=`|Modulus & assign|`x %= 2`|`x = x % 2`|
|`&=`|Bitwise AND & assign|`x &= 3`|`x = x & 3`|
|`|=`|Bitwise OR & assign|`x|
|`^=`|Bitwise XOR & assign|`x ^= 3`|`x = x ^ 3`|
|`<<=`|Left shift & assign|`x <<= 1`|`x = x << 1`|
|`>>=`|Right shift & assign|`x >>= 1`|`x = x >> 1`|
|`??=`|Assign if null|`x ??= 5`|`if (x == null) x = 5;`|

---

## 3. Real-World Example

A **bank account transaction system**:

```Dart
void main() {
  var balance = 1000;

  // Deposit
  balance += 500;
  print("After deposit: $balance");

  // Withdrawal
  balance -= 200;
  print("After withdrawal: $balance");

  // Interest (5%)
  balance *= 1.05.toInt();
  print("After interest: $balance");

  // Bonus if no balance set (using ??=)
  int? bonus;
  bonus ??= 100;
  print("Bonus: $bonus");

  // Deduct service fee
  balance ~/= 2;
  print("After service fee: $balance");
}

```

**Output Example:**

```Plain
After deposit: 1500
After withdrawal: 1300
After interest: 1365
Bonus: 100
After service fee: 682

```

---

⚡ This demo shows `=`, `+=`, `-=`, `*=`, `~/=`, and `??=` in action.