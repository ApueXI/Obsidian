---
Created: 2025-09-16T20:09
tags:
  - OOP
---
# 🎯 Dart Mixins Cheat Sheet

## 1. Full Explanation

- **Mixin** = a class whose methods and properties can be **reused in other classes** without using inheritance.
- Allows **code reuse** across **unrelated classes**.
- Keywords:
    - `mixin` → defines a mixin
    - `with` → applies a mixin to a class
- Unlike `extends` or `implements`:
    - Mixins **don’t create a parent-child relationship**
    - Mixins **cannot have constructors**

---

## 2. Basic Mixin Example

```Dart
mixin Logger {
  void log(String message) {
    print("LOG: $message");
  }
}

class User {
  String name;
  User(this.name);
}

class Admin extends User with Logger {
  Admin(String name) : super(name);

  void deleteUser() {
    log("$name deleted a user"); // use mixin method
  }
}

void main() {
  var admin = Admin("Alice");
  admin.deleteUser(); // LOG: Alice deleted a user
}

```

✅ `Admin` class **reuses Logger methods** without inheriting from it.

---

## 3. Multiple Mixins

```Dart
mixin Logger {
  void log(String msg) => print("LOG: $msg");
}

mixin Auth {
  void authenticate() => print("User authenticated");
}

class AppUser with Logger, Auth {
  String name;
  AppUser(this.name);
}

void main() {
  var user = AppUser("Bob");
  user.log("App started");       // LOG: App started
  user.authenticate();           // User authenticated
}

```

✅ Multiple mixins can be applied **in order** using commas.

---

## 4. Restricting Mixins to Certain Classes

- Use `**on**` keyword to restrict which classes a mixin can be applied to.

```Dart
class Vehicle {}

mixin Electric on Vehicle {
  void charge() => print("Charging electric vehicle");
}

class Car extends Vehicle with Electric {}

void main() {
  var car = Car();
  car.charge(); // Charging electric vehicle
}

```

✅ `Electric` can only be mixed into classes that **extend Vehicle**.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Define mixin|`mixin MixinName {}`|Cannot have constructors|
|Apply mixin|`class Child with Mixin1, Mixin2 {}`|Multiple mixins allowed|
|Restrict mixin|`mixin MixinName on BaseClass {}`|Only applies to subclasses of `BaseClass`|
|Difference from extends|`extends` = inheritance, `with` = reuse|Mixins do not create parent-child relationship|
|Use in method|Call directly like normal methods|`log()`, `authenticate()`|

---

## 6. Real-World Example

💡 **Flutter Example: Reusable Logging & Analytics**

```Dart
mixin Logger {
  void log(String msg) => print("LOG: $msg");
}

mixin Analytics {
  void track(String event) => print("Tracking event: $event");
}

class Screen with Logger, Analytics {
  String name;
  Screen(this.name);

  void open() {
    log("Opening screen $name");
    track("screen_opened");
  }
}

void main() {
  var homeScreen = Screen("Home");
  homeScreen.open();
  // Output:
  // LOG: Opening screen Home
  // Tracking event: screen_opened
}

```

✅ Mixins let you **share behavior** across multiple unrelated classes like screens, widgets, or services.