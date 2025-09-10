## Java Roadmap

### 🔰 1. **Basics & Foundations**

- What is Java? (JVM, JDK, JRE)
- Writing your first program (`HelloWorld.java`)
- Java file structure (class, `main` method)
- Compiling & running (`javac`, `java`)
- Variables & Data Types (primitive + reference)
- Type casting (implicit, explicit)
- Operators (arithmetic, relational, logical, bitwise, assignment)
- Input/Output with `System.in`, `System.out`

---

### 🔄 2. **Control Flow**

- `if`, `else if`, `else`
- `switch` (including Java 14+ switch expressions)
- Loops: `for`, `while`, `do while`
- Enhanced for loop (`for-each`)
- Jump statements: `break`, `continue`, `return`

---

### 🧮 3. **Methods (Functions)**

- Declaring & calling methods
- Parameters & return values
- Method overloading
- `static` methods
- Recursion
- Varargs (`...`)

---

### 🧱 4. **Object-Oriented Programming (OOP)**

- Classes & Objects
- Fields & Methods
- Constructors (default, parameterized, overloading)
- `this` keyword
- Encapsulation (getters & setters)
- Access Modifiers (`public`, `private`, `protected`, `default`)
- Inheritance (`extends`)
- Polymorphism (overriding, dynamic dispatch)
- `super` keyword
- Abstract Classes & Methods
- Interfaces (`implements`)
- Static variables & methods
- Nested & Inner classes
- `final` keyword (class, method, variable)

---

### 🧩 5. **Special Types**

- Enums (`enum`)
- Records (Java 14+)
- Wrapper Classes (`Integer`, `Double`, etc.)
- Autoboxing & Unboxing

---

### 📂 6. **Arrays & Collections (Core)**

- 1D arrays
- 2D arrays
- `Arrays` utility class (`sort`, `binarySearch`)
- Basic Collections (built-in in JDK):
    - `ArrayList`
    - `LinkedList`
    - `HashSet`, `TreeSet`
    - `HashMap`, `TreeMap`
    - `Stack`, `Queue`

---

### 🎯 7. **Strings & Text Handling**

- String basics (`length`, `substring`, `indexOf`, `replace`)
- String concatenation & immutability
- `StringBuilder` and `StringBuffer`
- String formatting (`String.format`, `printf`)

---

### 🔐 8. **Exception Handling**

- `try`, `catch`, `finally`
- `throw` & `throws`
- Checked vs Unchecked exceptions
- Custom exception classes

---

### 📚 9. **Packages & Modularization**

- Defining & importing packages
- `import` keyword
- Java modules (`module-info.java`, from Java 9+)

---

### ⏱️ 10. **Date & Time API**

- `java.util.Date` (legacy)
- `Calendar` (legacy)
- Modern API: `java.time.LocalDate`, `LocalTime`, `LocalDateTime`
- Duration & Period

---

### 🧮 11. **Math & Utility Classes**

- `Math` class (`pow`, `sqrt`, `max`, `min`, `random`)
- `Random` class
- `BigInteger`, `BigDecimal`

---

### 🧠 12. **Advanced OOP & Language Features**

- Interfaces with default & static methods
- Functional Interfaces (Java 8+)
- Lambda expressions
- Method references
- Anonymous classes
- Generics (`List<T>`, `Map<K,V>`)
- Wildcards (`?`, `extends`, `super`)

---

### 💾 13. **File I/O & Streams**

- `File` class
- Reading/Writing text files (`FileReader`, `FileWriter`, `BufferedReader`, `BufferedWriter`)
- Byte streams (`FileInputStream`, `FileOutputStream`)
- NIO.2 (`Paths`, `Files`)

---

### 🔄 14. **Streams & Functional Programming**

- `Stream` API (map, filter, reduce, collect)
- Parallel streams
- Optional (`Optional<T>`)

---

### ⚙️ 15. **Concurrency & Multithreading**

- `Thread` class & `Runnable` interface
- Synchronization (`synchronized` keyword, locks)
- Thread pools (`ExecutorService`)
- `Callable` & `Future`
- `volatile`, `AtomicInteger` (basic concurrency primitives)

---

### 🔍 16. **Reflection & Annotations**

- Reflection API (`Class`, `Method`, `Field`)
- Custom annotations
- Built-in annotations (`@Override`, `@Deprecated`, `@SuppressWarnings`)

---

### 🧰 17. **JVM & Memory Concepts**

- Stack vs Heap memory
- Garbage Collection (GC basics)
- `finalize()` (legacy, discouraged)
- Java Memory Model basics

---

### 🔄 18. **Modules & Deployment**

- JAR files (packaging, running `java -jar`)
- Modularization with `module-info.java`
- Classpath vs Modulepath

---

### 🌀 19. **Optional Built-in Extras**

- Regular Expressions (`java.util.regex`)
- Networking (`java.net.ServerSocket`, `Socket`)
- Serialization (`Serializable`, `ObjectOutputStream`)
- Basic GUI (Swing, AWT — though outdated but still core)

---

## ✅ What You Can Do with Just Core Java:

- Build console applications
- Implement data structures & algorithms
- File processing tools
- CLI utilities
- Network applications (sockets, simple servers)
- Multithreaded apps
- Basic desktop apps with Swing