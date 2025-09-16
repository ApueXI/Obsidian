---
Created: 2025-09-16T19:59
tags:
  - Functions
---
# 🔢 Dart Optional Positional Parameters Cheat Sheet

## 1. Full Explanation

- Optional **positional** parameters are wrapped in **square brackets** `**[ ]**`.
- They are **optional** when calling the function.
- If not provided → they are `null` (unless you give them a default).
- Useful for arguments that are not always needed.

---

### 🔹 Basic Example

```Dart
void printInfo(String name, [int? age]) {
  print("Name: $name, Age: ${age ?? "unknown"}");
}

void main() {
  printInfo("Alice");      // Name: Alice, Age: unknown
  printInfo("Bob", 30);    // Name: Bob, Age: 30
}

```

✅ `age` is optional.

---

### 🔹 With Default Value

```Dart
void greet(String name, [String suffix = ""]) {
  print("Hello $name$suffix");
}

void main() {
  greet("Charlie");          // Hello Charlie
  greet("Diana", "!");       // Hello Diana!
}

```

✅ Default values save you from null checks.

---

### 🔹 Multiple Optional Parameters

```Dart
void showMessage(String msg, [String prefix = ">>>", String suffix = "<<<"]) {
  print("$prefix $msg $suffix");
}

void main() {
  showMessage("Hello");                  // >>> Hello <<<
  showMessage("Hi", "--");               // -- Hi <<<
  showMessage("Yo", "--", "!!");         // -- Yo !!
}

```

✅ If you provide fewer arguments, Dart uses defaults for the rest.

---

### 🔹 Mixing Required & Optional

```Dart
void describe(String name, [int? age, String? city]) {
  print("Name: $name, Age: ${age ?? "?"}, City: ${city ?? "?"}");
}

void main() {
  describe("Eve");                      // Name: Eve, Age: ?, City: ?
  describe("Frank", 25);                // Name: Frank, Age: 25, City: ?
  describe("Grace", 30, "London");      // Name: Grace, Age: 30, City: London
}

```

---

## 2. Summary Table

|Syntax|Example|Call|Result|
|---|---|---|---|
|Basic|`fn(a, [b])`|`fn(1)`|`b=null`|
|Default|`fn(a, [b=2])`|`fn(1)`|`b=2`|
|Multiple|`fn(a, [b=1,c=2])`|`fn(5,10)`|`c=2`|
|Nullable|`fn([int? x])`|`fn()`|`x=null`|

---

## 3. Real-World Example

💡 **Flutter SnackBar with Optional Style**

```Dart
import 'package:flutter/material.dart';

void showSnack(BuildContext context, String message,
    [Color bgColor = Colors.blue, int durationSec = 2]) {
  final snackBar = SnackBar(
    content: Text(message),
    backgroundColor: bgColor,
    duration: Duration(seconds: durationSec),
  );
  ScaffoldMessenger.of(context).showSnackBar(snackBar);
}

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: Builder(
          builder: (context) => ElevatedButton(
            onPressed: () {
              showSnack(context, "Default Snack"); // uses default color & time
              showSnack(context, "Custom Snack", Colors.red, 5);
            },
            child: Text("Show Snack"),
          ),
        ),
      ),
    ),
  ));
}

```

✅ Uses optional positional params to allow flexibility in styling.