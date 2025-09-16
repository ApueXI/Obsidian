---
Created: 2025-09-16T19:44
tags:
  - Basic-Syntax
---
# 🔢 Dart Data Types Cheat Sheet (`int`, `double`, `String`, `bool`, `num`)

## 1. Full Explanation

Dart is **statically typed with type inference**. That means variables have a fixed type, but you don’t always need to write it explicitly (`var` will infer).

---

### 🔹 `int`

- Represents **whole numbers** (no decimal).
- Arbitrary precision in Dart 2.0+ (no fixed 32-bit/64-bit overflow issues).

```Dart
int age = 25;
int hex = 0xFF;   // hex literal = 255

```

---

### 🔹 `double`

- Represents **64-bit floating-point numbers** (IEEE 754 standard).
- Used for decimals and fractional numbers.

```Dart
double pi = 3.14159;
double price = 99.99;

```

---

### 🔹 `num`

- **Superclass of both** `**int**` **and** `**double**`.
- Useful when a variable can be either an integer or a decimal.

```Dart
num score = 95;     // int
score = 95.5;       // double (still valid, since num covers both)

```

---

### 🔹 `String`

- Sequence of UTF-16 characters.
- Single quotes `'...'` or double quotes `"..."`.
- Supports string interpolation with `$`.

```Dart
String name = "Alice";
String greeting = 'Hello, $name!';    // interpolation
String multiLine = '''
This is
a multi-line string.
''';

```

---

### 🔹 `bool`

- Only values: `true` or `false`.
- Commonly used in conditions and logical expressions.

```Dart
bool isLoggedIn = true;
bool hasPermission = false;

```

---

### 🔹 Conversion Between Types

```Dart
// int <-> double
int x = 10;
double y = x.toDouble();   // 10.0
int z = y.toInt();         // 10

// String <-> int
String s = "123";
int n = int.parse(s);      // 123
String s2 = n.toString();  // "123"

// String <-> double
double d = double.parse("3.14");   // 3.14
String d2 = d.toStringAsFixed(2);  // "3.14"

// num auto works with both
num a = 5;
num b = 5.5;

```

---

## 2. Summary Table (Quick Reference)

|Type|Example|Notes|
|---|---|---|
|`int`|`42`, `0xFF`|Whole numbers, no decimals.|
|`double`|`3.14`, `-0.5`|64-bit floating-point numbers.|
|`num`|`42` or `3.14`|Parent of int & double.|
|`String`|`"Hello"`|UTF-16 text, supports interpolation.|
|`bool`|`true`, `false`|Boolean values.|

---

## 3. Real-World Example

A small Dart program using all five types:

```Dart
void main() {
  int age = 25;
  double height = 5.9;
  num score = 95.5; // could be int or double
  String name = "Alice";
  bool isMember = true;

  print("User Info:");
  print("Name: $name");
  print("Age: $age years");
  print("Height: $height ft");
  print("Score: $score");
  print("Membership: ${isMember ? "Active" : "Inactive"}");
}

```

**Example Output:**

```Plain
User Info:
Name: Alice
Age: 25 years
Height: 5.9 ft
Score: 95.5
Membership: Active

```