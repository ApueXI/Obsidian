---
Created: 2025-09-16T19:02
tags:
  - Introduction-&-Basics
---
# ⚙️ Dart Installation & Running Cheat Sheet

## 1. Full Explanation

### 🔹 Installing Dart

There are multiple ways to get Dart:

- **With Flutter SDK** (recommended for Flutter devs)
    
    Dart comes bundled automatically, no extra install.
    
- **Standalone Dart SDK** (for CLI tools or server apps)
    - Download: https://dart.dev/get-dart
    - Or install via package manager:
        - **Windows**: Chocolatey → `choco install dart-sdk`
        - **macOS**: Homebrew → `brew tap dart-lang/dart && brew install dart`
        - **Linux (Debian/Ubuntu)**:
            
            ```Bash
            sudo apt update -y
            sudo apt install apt-transport-https
            sudo sh -c 'wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
            sudo sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
            sudo apt update -y
            sudo apt install dart
            
            ```
            

---

### 🔹 Running Dart Programs

- **Basic run (interpreted via VM, JIT mode)**
    
    ```Bash
    dart run my_program.dart
    
    ```
    
- **Running without specifying file (auto main.dart)**
    
    If you’re in a Dart project directory with `bin/main.dart`:
    
    ```Bash
    dart run
    
    ```
    

---

### 🔹 Compiling Dart Programs

- **Compile to native executable (AOT):**
    
    ```Bash
    dart compile exe my_program.dart
    ./my_program   # run executable
    
    ```
    
- **Compile to JavaScript (for web):**
    
    ```Bash
    dart compile js my_program.dart -o my_program.js
    
    ```
    
- **Compile to optimized snapshot (fast startup):**
    
    ```Bash
    dart compile aot-snapshot my_program.dart -o my_program.aot
    
    ```
    
- **Compile to Kernel IR (for VM use):**
    
    ```Bash
    dart compile kernel my_program.dart -o my_program.dill
    
    ```
    

---

### 🔹 Project Management

- **Initialize a new Dart project**
    
    ```Bash
    dart create my_app
    cd my_app
    dart run
    
    ```
    
- **Dependency management** (via `pubspec.yaml`):
    
    ```Bash
    dart pub get
    dart pub add http   # add package
    
    ```
    

---

## 2. Summary Table (Quick Reference)

|Command|Purpose|
|---|---|
|`dart run file.dart`|Run a Dart file (JIT mode).|
|`dart run`|Run project entry (`bin/main.dart`).|
|`dart compile exe file.dart`|Compile to native executable.|
|`dart compile js file.dart -o out.js`|Compile to JavaScript for web.|
|`dart compile aot-snapshot file.dart`|Compile to optimized AOT snapshot.|
|`dart compile kernel file.dart`|Compile to Kernel IR (VM).|
|`dart create my_app`|Create a new Dart project.|
|`dart pub get`|Install dependencies.|
|`dart pub add <package>`|Add new dependency.|

---

## 3. Real-World Example

Let’s say you want to build a **CLI tool** in Dart that prints a greeting:

**File:** `bin/hello.dart`

```Dart
void main(List<String> args) {
  final name = args.isNotEmpty ? args[0] : "World";
  print("Hello, $name! This is Dart in action 🚀");
}

```

### Run in Dev (JIT):

```Bash
dart run bin/hello.dart Alice
# Output: Hello, Alice! This is Dart in action 🚀

```

### Compile for Prod (AOT):

```Bash
dart compile exe bin/hello.dart -o hello
./hello Bob
# Output: Hello, Bob! This is Dart in action 🚀

```

👉 Now you’ve got a **fast native executable** you can share without needing Dart installed.