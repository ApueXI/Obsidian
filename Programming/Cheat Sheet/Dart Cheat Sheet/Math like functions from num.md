---
Created: 2025-09-16T20:31
tags:
  - Dart-Core-Library-(no-external-imports)
---
# 🎯 Dart `num` & Math-Like Functions Cheat Sheet

## 1. Full Explanation

- `**num**` is the base class for **numeric types**: `int` and `double`.
- Provides **common math operations** and **helper methods**.
- Useful for **calculations, bounds, rounding, and comparisons**.

---

## 2. Common `num` Methods

|Method|Description|Example|
|---|---|---|
|`abs()`|Absolute value|`(-5).abs()` → 5|
|`ceil()`|Smallest integer ≥ number|`3.2.ceil()` → 4|
|`floor()`|Largest integer ≤ number|`3.7.floor()` → 3|
|`round()`|Round to nearest integer|`3.5.round()` → 4|
|`truncate()`|Remove fractional part|`3.7.truncate()` → 3|
|`clamp(min, max)`|Restrict number to range|`5.clamp(1, 4)` → 4|
|`remainder(n)`|Remainder after division|`7.remainder(3)` → 1|
|`toInt()`|Convert to integer|`3.9.toInt()` → 3|
|`toDouble()`|Convert to double|`3.toDouble()` → 3.0|
|`sign`|Sign of number: -1, 0, 1|`(-10).sign` → -1|
|`isFinite`|Checks if finite|`(1/0).isFinite` → false|
|`isInfinite`|Checks if infinite|`(1/0).isInfinite` → true|
|`isNaN`|Checks if not-a-number|`(0/0).isNaN` → true|

---

## 3. Example Usage

```Dart
void main() {
  num a = -3.7;
  print(a.abs());       // 3.7
  print(a.ceil());      // -3
  print(a.floor());     // -4
  print(a.round());     // -4
  print(a.truncate());  // -3
  print(a.clamp(-2, 2)); // -2

  num b = 7;
  print(b.remainder(3)); // 1
  print(b.sign);          // 1
}

```

---

## 4. Using `min`, `max`

```Dart
import 'dart:math';

void main() {
  print(min(5, 10));  // 5
  print(max(5, 10));  // 10
  print(sqrt(16));    // 4.0
  print(pow(2, 3));   // 8
}

```

- `min(a, b)`, `max(a, b)` → from `dart:math`
- `sqrt()`, `pow()`, `sin()`, `cos()` → other math operations

---

## 5. Summary Table

|Method|Class|Purpose|
|---|---|---|
|`abs()`, `ceil()`, `floor()`, `round()`, `truncate()`|`num`|Rounding / absolute value|
|`clamp(min, max)`|`num`|Limit value to a range|
|`remainder(n)`|`num`|Remainder after division|
|`toInt()`, `toDouble()`|`num`|Convert type|
|`sign`, `isFinite`, `isInfinite`, `isNaN`|`num`|Number properties|
|`min(a,b)`, `max(a,b)`|`dart:math`|Compare two numbers|
|`sqrt(x)`, `pow(x,y)`, `sin(x)`, `cos(x)`|`dart:math`|Standard math functions|

---

## 6. Real-World Example

💡 **Clamping and rounding a score**

```Dart
void main() {
  double score = 87.6;

  // Round and clamp between 0 and 100
  double finalScore = score.round().clamp(0, 100).toDouble();

  print(finalScore); // 88
}

```

✅ Combines `round()` + `clamp()` for **safe numeric values**.