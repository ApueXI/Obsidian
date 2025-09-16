---
Created: 2025-09-16T20:22
tags:
  - Advance-Concepts
---
# 🎯 Dart 3 Records Cheat Sheet

## 1. Full Explanation

- **Records** are **fixed-size, immutable tuples** that can hold multiple values of **different types**.
- Syntax: `(Type1, Type2, ...)` for **positional fields**, optionally **named fields** `(Type1 x: value, Type2 y: value)`.
- Benefits:
    - Lightweight alternative to **creating small classes**
    - Supports **pattern matching** in Dart 3
    - **Immutable** by default

---

## 2. Basic Positional Record

```Dart
void main() {
  (int, String) record = (1, "Alice");

  print(record.$1); // 1
  print(record.$2); // Alice
}

```

✅ Access positional elements using **$1, $2, $3…**.

---

## 3. Named Fields Record

```Dart
void main() {
  (int id, String name) record = (id: 1, name: "Alice");

  print(record.id);   // 1
  print(record.name); // Alice
}

```

✅ Named fields make **code more readable** than positional indexes.

---

## 4. Functions Returning Records

```Dart
(int, int) calculateSumAndProduct(int a, int b) {
  return (a + b, a * b);
}

void main() {
  var result = calculateSumAndProduct(3, 4);
  print(result.$1); // 7 (sum)
  print(result.$2); // 12 (product)
}

```

✅ Useful for returning **multiple values without creating a class**.

---

## 5. Destructuring Records

```Dart
void main() {
  var record = (id: 1, name: "Alice");

  var (id: myId, name: myName) = record;
  print(myId);   // 1
  print(myName); // Alice
}

```

✅ Records support **destructuring** for cleaner code.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Positional record|`(Type1, Type2) record = (value1, value2);`|Access via `$1, $2`|
|Named fields|`(Type1 name1, Type2 name2) record = (name1: val1, name2: val2);`|Access via names|
|Function return|`(Type1, Type2) func() => (val1, val2);`|Return multiple values|
|Destructuring|`var (name1: a, name2: b) = record;`|Extract fields directly|
|Immutable|All record fields are `final` by default|Cannot reassign elements|

---

## 7. Real-World Example

💡 **API Response Simulation**

```Dart
(int status, String message) fetchUser(int id) {
  if (id == 0) return (404, "User not found");
  return (200, "User fetched");
}

void main() {
  var response = fetchUser(1);
  print("Status: ${response.$1}, Message: ${response.$2}"); // Status: 200, Message: User fetched

  var (status, message) = fetchUser(0);
  print("Status: $status, Message: $message"); // Status: 404, Message: User not found
}

```

✅ Records make **returning multiple values simple** without creating extra classes.