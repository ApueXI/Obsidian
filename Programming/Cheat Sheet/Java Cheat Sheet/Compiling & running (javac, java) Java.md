---
Created: 2025-08-25T19:25
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 Compilation & Execution Workflow

1. **Write Source Code**
    - Save your code in a file ending with `.java`.
    - Example: `HelloWorld.java`.
2. **Compile with** `**javac**`
    
    ```Bash
    javac HelloWorld.java
    
    ```
    
    - `javac` = Java Compiler.
    - Converts `.java` (source code) → `.class` (bytecode).
    - Creates a file named `HelloWorld.class`.
3. **Run with** `**java**`
    
    ```Bash
    java HelloWorld
    
    ```
    
    - `java` = Java Launcher.
    - Runs the **class file** on the JVM.
    - Notice: **Do not add** `**.class**` when running.
4. **Bytecode Portability**
    - The `.class` file is **platform-independent**.
    - Runs on **any OS with JVM** (Windows, Linux, macOS).

---

### 🔹 Common Gotchas

- File name **must match** public class name.
- Running with `java HelloWorld.class` ❌ → error. Correct: `java HelloWorld`.
- If using **packages**, you must run with full package name:
    
    ```Bash
    javac com/example/App.java
    java com.example.App
    
    ```
    
- Multiple `.class` files may be generated if your program has multiple classes.

---

## 2. 📊 Summary Table

|Command|Purpose|Example|
|---|---|---|
|`javac <FileName>.java`|Compiles source code → bytecode|`javac HelloWorld.java`|
|`java <ClassName>`|Runs the compiled bytecode|`java HelloWorld`|
|`java -version`|Checks installed Java version|`java -version`|
|`javac -d <dir>`|Compiles into a specific output directory|`javac -d bin HelloWorld.java`|

---

## 3. 🌍 Real-World Example

Imagine a **multi-file project**:

📂 Project Structure

```Plain
src/
 ├── MainApp.java
 └── utils/
      └── Helper.java

```

**MainApp.java**

```Java
package src;

import src.utils.Helper;

public class MainApp {
    public static void main(String[] args) {
        Helper.sayHi("Java Developer");
    }
}

```

**Helper.java**

```Java
package src.utils;

public class Helper {
    public static void sayHi(String name) {
        System.out.println("Hello, " + name + "!");
    }
}

```

### Compile & Run

```Bash
javac src/MainApp.java src/utils/Helper.java
java src.MainApp

```

✅ Output:

```Plain
Hello, Java Developer!

```

This shows how `javac` handles **multiple files** and how `java` executes the **main class** with correct package structure.