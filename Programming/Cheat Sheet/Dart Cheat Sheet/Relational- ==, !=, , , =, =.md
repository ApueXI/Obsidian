---
Created: 2025-09-16T19:48
tags:
  - Operators
---
# 🧩 Dart Relational Operators Cheat Sheet

## 1. Full Explanation

Relational operators are used to **compare two values** and return a `bool` (`true` or `false`).

### 🔹 Equality & Inequality

- `==` → true if values are equal.
- `!=` → true if values are not equal.

```Dart
print(5 == 5);   // true
print(5 != 3);   // true
print("hi" == "hi"); // true

```

⚠️ In Dart, `==` calls the `.==` method of objects, so classes can **override equality**.

---

### 🔹 Comparison Operators

- `<` → less than
- `>` → greater than
- `<=` → less than or equal to
- `>=` → greater than or equal to

```Dart
print(5 < 10);   // true
print(5 > 10);   // false
print(5 <= 5);   // true
print(10 >= 5);  // true

```

---

### 🔹 With Strings

- Strings compare lexicographically (like dictionary order).

```Dart
print("apple" == "apple"); // true
print("apple" != "banana"); // true
print("apple" < "banana");  // true (because 'a' < 'b')

```

---

### 🔹 With Null

- `null` can be compared, but only equal to `null`.

```Dart
print(null == null); // true
print(null != 5);    // true

```

---

### 🔹 Custom Objects

- If you want `==` to behave meaningfully, override `==` and `hashCode`.

```Dart
class Person {
  String name;
  Person(this.name);

  @override
  bool operator ==(Object other) =>
      other is Person && other.name == name;

  @override
  int get hashCode => name.hashCode;
}

void main() {
  var p1 = Person("Alice");
  var p2 = Person("Alice");
  print(p1 == p2); // true (after overriding)
}

```

---

## 2. Summary Table (Quick Reference)

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`==`|Equal to|`5 == 5`|`true`|
|`!=`|Not equal to|`5 != 3`|`true`|
|`<`|Less than|`3 < 5`|`true`|
|`>`|Greater than|`5 > 3`|`true`|
|`<=`|Less than or equal|`5 <= 5`|`true`|
|`>=`|Greater than or equal|`5 >= 4`|`true`|

---

## 3. Real-World Example

A **grade checker**:

```Dart
void main() {
  var score = 85;

  if (score >= 90) {
    print("Grade: A");
  } else if (score >= 80 && score < 90) {
    print("Grade: B");
  } else if (score >= 70) {
    print("Grade: C");
  } else {
    print("Grade: F");
  }

  // Check equality
  var bonusPoints = 5;
  if (bonusPoints != 0) {
    print("You received bonus points!");
  }
}

```

**Output Example:**

```Plain
Grade: B
You received bonus points!

```

---

⚡ This example shows `>=`, `<`, `!=`, and `==` in a practical scenario.