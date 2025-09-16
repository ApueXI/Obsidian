---
Created: 2025-09-16T19:42
tags:
  - Introduction-&-Basics
---
# 📦 Dart SDK Structure Cheat Sheet

## 1. Full Explanation

When you install Dart (either standalone or bundled with Flutter), you get the **Dart SDK** — a set of tools, core libraries, and runtime needed to write, run, and compile Dart programs.

### 🔹 Key Components

1. **Dart VM (Virtual Machine)**
    - Executes Dart code in **JIT mode** (useful for development & hot reload).
    - Runs `.dart` files directly using `dart run`.
2. **Ahead-of-Time (AOT) Compiler**
    - Converts Dart code into **native machine code**.
    - Used in Flutter **release builds**.
3. **Just-in-Time (JIT) Compiler**
    - Compiles Dart to machine code **on the fly**.
    - Enables **fast iteration** & hot reload.
4. **Dart Core Libraries**
    - Standard APIs: `dart:core`, `dart:async`, `dart:io`, `dart:convert`, etc.
    - These are like the “standard library” in Python (`sys`, `os`) or C++ STL.
5. **dart2js (Dart-to-JS Compiler)**
    - Converts Dart code into **JavaScript** for running in browsers.
6. **dartdev / dart tool**
    - The CLI interface (`dart run`, `dart compile`, `dart create`, `dart pub`).
7. **pub (Package Manager)**
    - Handles dependencies (`dart pub get`, `dart pub add`).
    - Uses pub.dev for packages (similar to npm for Node.js).
8. **Analyzer & Formatter**
    - **dart analyze** → Static code analysis.
    - **dart format** → Auto-format code.

---

### 🔹 Folder Structure of the SDK

If you peek inside the Dart SDK installation folder, you’ll usually find:

```Plain
dart-sdk/
│
├── bin/            # Executables (dart, pub, dart2js, dartaotruntime)
├── include/        # C headers (for embedding Dart VM in C/C++)
├── lib/            # Dart core libraries (dart:core, dart:io, etc.)
│   ├── async/
│   ├── collection/
│   ├── convert/
│   ├── core/
│   ├── io/
│   └── ...
├── runtime/        # Dart VM and runtime files
├── version         # Version file (e.g., "3.5.0")
└── LICENSE

```

---

## 2. Summary Table (Quick Reference)

|Component|Purpose|
|---|---|
|**Dart VM**|Runs Dart code in JIT mode.|
|**AOT Compiler**|Produces native executables (fast production).|
|**JIT Compiler**|Enables hot reload & quick iteration.|
|**Core Libraries**|Built-in standard APIs (`dart:core`, `dart:io`).|
|**dart2js**|Compiles Dart → JavaScript for browsers.|
|**pub**|Package manager for Dart & Flutter.|
|**Analyzer**|Linter/static analysis (`dart analyze`).|
|**Formatter**|Auto-formatting tool (`dart format`).|
|**bin/**|CLI tools (`dart`, `pub`, `dart2js`, etc.).|
|**lib/**|Dart core libraries source.|
|**runtime/**|VM binaries & runtime data.|

---

## 3. Real-World Example

Let’s say you install the **standalone Dart SDK** and want to:

1. **Check version**
    
    ```Bash
    dart --version
    
    ```
    
    Output:
    
    ```Plain
    Dart SDK version: 3.5.0 (stable)
    
    ```
    
2. **Analyze a project** (uses analyzer)
    
    ```Bash
    dart analyze
    
    ```
    
3. **Format code** (uses formatter)
    
    ```Bash
    dart format lib/
    
    ```
    
4. **Compile to native exe** (uses AOT compiler)
    
    ```Bash
    dart compile exe bin/main.dart -o app
    ./app
    
    ```
    
5. **Compile to JS for web** (uses dart2js)
    
    ```Bash
    dart compile js bin/main.dart -o app.js
    
    ```
    

👉 Each of these commands corresponds directly to **tools included in the SDK**.