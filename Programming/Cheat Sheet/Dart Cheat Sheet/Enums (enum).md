---
Created: 2025-09-16T20:10
tags:
  - OOP
---
# 🎯 Dart Enums Cheat Sheet

## 1. Full Explanation

- **Enum** = a special **class representing a fixed set of values**.
- Useful for:
    - Representing **options, states, or categories**
    - Avoiding **magic strings/numbers**
- Enums are **type-safe**.
- Syntax: `enum Name { value1, value2, value3 }`

---

## 2. Basic Enum Example

```Dart
enum Color { red, green, blue }

void main() {
  var c = Color.red;

  print(c);        // Color.red
  print(c.index);  // 0
}

```

✅ `index` returns the **position** of the enum value.

---

## 3. Using Enums in Switch Statements

```Dart
enum Status { pending, approved, rejected }

void checkStatus(Status status) {
  switch (status) {
    case Status.pending:
      print("Pending approval");
      break;
    case Status.approved:
      print("Approved");
      break;
    case Status.rejected:
      print("Rejected");
      break;
  }
}

void main() {
  checkStatus(Status.approved); // Approved
}

```

✅ Enums make **conditional logic readable and safe**.

---

## 4. Adding Properties & Methods (Dart 2.17+)

```Dart
enum Planet {
  mercury(3.3e23),
  venus(4.87e24),
  earth(5.97e24);

  final double mass; // kg
  const Planet(this.mass); // constructor

  void showMass() {
    print("Mass: $mass kg");
  }
}

void main() {
  Planet.earth.showMass(); // Mass: 5.97e24 kg
}

```

✅ Enums can have **fields, constructors, and methods**.

---

## 5. Iterating Over Enum Values

```Dart
enum Direction { north, south, east, west }

void main() {
  for (var dir in Direction.values) {
    print(dir);
  }
  // Output:
  // Direction.north
  // Direction.south
  // Direction.east
  // Direction.west
}

```

✅ Use `.values` to get a **list of all enum members**.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Define enum|`enum Name { value1, value2 }`|Fixed set of values|
|Access value|`EnumName.value`|Type-safe|
|Index|`value.index`|Position in declaration|
|Switch usage|`switch(value)`|Clear conditional handling|
|Properties/methods|`enum Name { ... }; final field; const constructor;`|Dart 2.17+|
|Iterate|`EnumName.values`|Loop through all members|

---

## 7. Real-World Example

💡 **Order Status Example**

```Dart
enum OrderStatus { pending, shipped, delivered, canceled }

class Order {
  String id;
  OrderStatus status;
  Order(this.id, this.status);

  void showStatus() {
    print("Order $id is ${status.name}");
  }
}

void main() {
  var order = Order("12345", OrderStatus.shipped);
  order.showStatus(); // Order 12345 is shipped
}

```

✅ Shows **type-safe status handling** for orders instead of strings.