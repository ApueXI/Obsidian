---
Created: 2025-09-16T20:26
tags:
  - Null-Safety-Deep-Dive
---
# 🎯 Dart Non-Nullable Defaults Cheat Sheet

## 1. Full Explanation

- With **null safety**, Dart variables are **non-nullable by default**.
- Declaring a variable without `?` means it **cannot hold null**.
- You must **initialize it at declaration** or use `late` if initialization is deferred.
- Helps **prevent null-related runtime errors**.

---

## 2. Non-Nullable Variable Declaration

```Dart
void main() {
  String name = "Alice"; // non-nullable
  // name = null;        // ❌ Compile-time error
  print(name);
}

```

✅ Non-nullable variables **cannot be null**.

---

## 3. Using Default Values

- When a **parameter is non-nullable**, you can provide a **default value**:

```Dart
void greet({String name = "Guest"}) {
  print("Hello, $name");
}

void main() {
  greet();           // Hello, Guest
  greet(name: "Bob"); // Hello, Bob
}

```

✅ Ensures **non-nullable parameters always have a value**.

---

## 4. Non-Nullable Fields in Classes

```Dart
class User {
  String name;
  int age;

  User({this.name = "Anonymous", this.age = 18});
}

void main() {
  var user = User();
  print("${user.name}, ${user.age}"); // Anonymous, 18
}

```

✅ Provides **safe defaults** for non-nullable fields.

---

## 5. Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Non-nullable variable|`String name = "Alice";`|Cannot assign null|
|Non-nullable parameter|`void greet({String name = "Guest"})`|Default value ensures safety|
|Non-nullable field|`String name;`|Must be initialized at declaration or in constructor|
|Late non-nullable|`late String name;`|Can defer initialization safely|

---

## 6. Real-World Example

💡 **Flutter Button Label Default**

```Dart
class Button {
  String label;
  Button({this.label = "Click Me"});
}

void main() {
  var btn1 = Button();
  var btn2 = Button(label: "Submit");

  print(btn1.label); // Click Me
  print(btn2.label); // Submit
}

```

✅ Using **non-nullable defaults** avoids runtime null errors and simplifies logic.