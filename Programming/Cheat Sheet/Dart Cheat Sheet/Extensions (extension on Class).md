---
Created: 2025-09-16T20:21
tags:
  - Advance-Concepts
---
# 🎯 Dart Extensions Cheat Sheet

## 1. Full Explanation

- **Extensions** let you **add methods, getters, or operators** to any class, including **built-in classes**.
- Syntax:

```Dart
extension ExtensionName on ClassName {
  // new methods or getters
}

```

- Benefits:
    - Keeps code **clean and modular**
    - Avoids **subclassing just to add methods**
    - Works on **any type**

---

## 2. Basic Example

```Dart
extension StringExtensions on String {
  bool get isPalindrome {
    String reversed = split('').reversed.join('');
    return this == reversed;
  }
}

void main() {
  String word = "level";
  print(word.isPalindrome); // true
}

```

✅ Adds a **custom getter** `**isPalindrome**` to `String`.

---

## 3. Adding Methods

```Dart
extension IntExtensions on int {
  int squared() => this * this;
}

void main() {
  int num = 5;
  print(num.squared()); // 25
}

```

✅ Extensions can add **methods** just like regular class methods.

---

## 4. Extensions with Generics

```Dart
extension ListExtensions<T> on List<T> {
  T? second() => length >= 2 ? this[1] : null;
}

void main() {
  var nums = [1, 2, 3];
  print(nums.second()); // 2

  var words = ["a"];
  print(words.second()); // null
}

```

✅ Works with **generic classes** like `List<T>`.

---

## 5. Overriding Existing Methods

- Extensions **cannot override existing methods** of a class.
- If a method exists, the original method takes precedence.

```Dart
extension StringExt on String {
  String toUpper() => "CUSTOM"; // won't override existing `toUpperCase()`
}

```

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Define extension|`extension Name on Class { ... }`|Add methods/getters|
|Add method|`ReturnType methodName() { ... }`|Works like regular class method|
|Add getter|`Type get name => ...;`|Provides computed property|
|Generics|`extension Name<T> on Class<T> { ... }`|Works with generic classes|
|Limitations|Cannot override existing methods|Only adds new functionality|

---

## 7. Real-World Example

💡 **DateTime Extensions**

```Dart
extension DateTimeFormatting on DateTime {
  String get formatted => "${this.day}-${this.month}-${this.year}";
}

void main() {
  DateTime now = DateTime(2025, 9, 16);
  print(now.formatted); // 16-9-2025
}

```

✅ Makes **code more readable** by adding custom formatting directly to `DateTime`.