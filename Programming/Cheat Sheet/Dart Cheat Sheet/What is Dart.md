---
Created: 2025-09-16T19:00
tags:
  - Introduction-&-Basics
---
# 🐦 Dart Language Cheat Sheet (for Flutter)

## 1. Full Explanation

### What is Dart?

Dart is the programming language used to build **Flutter apps**. It’s designed for **UI-first development** and combines features of scripting languages (fast iteration) with compiled languages (performance).

---

### 🔹 Compilation

- **JIT (Just-in-Time):**
    - Used during **development**.
    - Enables **hot reload** in Flutter (fast app changes without full rebuild).
    - Compiles Dart source into machine code at runtime.
- **AOT (Ahead-of-Time):**
    - Used for **production builds**.
    - Dart is compiled **directly into native ARM or x64 machine code**.
    - Ensures high-performance apps with minimal startup time.

---

### 🔹 Type System (Optionally Typed → Now Sound Null Safety)

- **Optionally Typed:** Dart started as **optional typing**, where you could omit types (`var x = 5`).
- **Now with Null Safety (Dart 2.12+):**
    - By default, variables **cannot be null** unless explicitly declared with `?`.
    - This prevents common null-reference errors.

Example:

```Dart
String name = "Flutter";   // non-nullable
String? nickname;          // nullable, can be null

```

---

### 🔹 Key Features

- **Compiled** → Runs native on iOS, Android, desktop, web.
- **UI-optimized** → Built with Flutter in mind, reactive & declarative.
- **Fast iteration** → Hot reload via JIT.
- **Production-ready** → High performance via AOT.
- **Null Safety** → Prevents “null pointer exceptions.”
- **Cross-platform** → One codebase for mobile, web, desktop.

---

## 2. Summary Table (Quick Reference)

|Feature|Explanation|
|---|---|
|**Compiled**|Dart compiles to **native machine code** (AOT) and **runs in VM** (JIT).|
|**JIT (Dev)**|Just-in-Time, enables **hot reload** for rapid dev cycles.|
|**AOT (Prod)**|Ahead-of-Time, compiles to **fast, optimized native code**.|
|**Optionally Typed**|Type inference works, but you can declare explicit types.|
|**Null Safety**|Variables are **non-nullable by default**. Use `?` for nullable.|
|**Cross-Platform**|Runs on **iOS, Android, Web, Desktop**.|
|**UI-First**|Designed for **Flutter apps** with reactive, declarative UI.|

---

## 3. Real-World Example (Flutter Widget)

Here’s a **real Flutter widget** showing Dart’s null safety, types, and Flutter’s hot reload friendliness:

```Dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    // Non-nullable String
    String title = "Hello, Dart with Flutter!";

    // Nullable String
    String? subtitle;
    subtitle ??= "Runs with Null Safety";  // Assign only if null

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text(title)),
        body: Center(child: Text(subtitle)),
      ),
    );
  }
}

```

**What this does:**

- Shows Dart’s **null safety** (`String? subtitle`).
- Uses Flutter’s **UI-first design**.
- Can be hot reloaded instantly (JIT).
- In production, compiled into **native ARM/x64 binary** (AOT).