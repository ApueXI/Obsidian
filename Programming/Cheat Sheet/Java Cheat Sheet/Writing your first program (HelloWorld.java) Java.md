---
Created: 2025-08-25T19:24
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 Steps to Write Your First Java Program

1. **Install JDK**
    - Download and install the latest JDK (e.g., Java 17 or 21 LTS).
    - Verify installation:
        
        ```Bash
        java -version
        javac -version
        
        ```
        
2. **Create a Source File**
    - Create a file named **HelloWorld.java** (file name **must match** the class name).
3. **Write the Code**
    
    ```Java
    public class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello, World!");
        }
    }
    
    ```
    
    - `**public class HelloWorld**` → Defines a class named `HelloWorld`.
    - `**public static void main(String[] args)**` → Entry point of every Java application.
    - `**System.out.println()**` → Prints text to the console.
4. **Compile the Program**
    
    ```Bash
    javac HelloWorld.java
    
    ```
    
    - This generates `HelloWorld.class` (bytecode).
5. **Run the Program**
    
    ```Bash
    java HelloWorld
    
    ```
    
    - ✅ Output:
        
        ```Plain
        Hello, World!
        
        ```
        

---

### 🔹 Gotchas / Important Notes

- The **file name must match the class name** (case-sensitive).
- Unlike C++ or Python, Java enforces a **single entry point** → `main` method.
- Java bytecode (`.class`) is **portable** — can run on any OS with JVM.

---

## 2. 📊 Summary Table (Quick Reference)

|Step|Command / Code|Purpose|
|---|---|---|
|1|`javac HelloWorld.java`|Compiles source to bytecode|
|2|`java HelloWorld`|Runs the compiled bytecode|
|Code|`System.out.println("Hello, World!");`|Prints output to console|

---

## 3. 🌍 Real-World Example

Think of **HelloWorld.java** as the “proof of installation.”

- When a company hires a new Java developer, the first thing they’ll often do is test if their setup works by running `HelloWorld.java`.
- Once successful, you can start building **real-world projects** like:
    - Backend services (Spring Boot)
    - Mobile apps (Android uses Java/Kotlin)
    - Enterprise applications (JSP, Servlets, etc.)