## CSharp Road Map

### 🔰 1. **Basics & Syntax**

- Hello World
- Variables & Constants
- Data Types (int, float, double, char, bool, string)
- Type Conversion & Casting
- Comments
- Operators (Arithmetic, Relational, Logical, Assignment, Bitwise)
- Input/Output using `Console.ReadLine()` and `Console.WriteLine()`

---

### 🔄 2. **Control Flow**

- Conditional Statements (`if`, `else if`, `else`, `switch`)
- Loops:
    - `for`
    - `while`
    - `do while`
    - `foreach`
- Jump Statements:
    - `break`
    - `continue`
    - `return`
    - `goto` (rarely used, but still in the language)

---

### 🧮 3. **Methods (Functions)**

- Method Declaration and Calling
- Method Overloading
- Parameters:
    - `ref`, `out`, `in`, `params`
- Default Parameters
- Return Types
- Recursion

---

### 🧱 4. **Object-Oriented Programming (OOP)**

- Classes & Objects
- Fields & Properties
- Constructors (Default, Parameterized, Static)
- Encapsulation (Private/Public)
- Inheritance
- Method Overriding (`virtual`, `override`)
- `base` keyword
- Polymorphism
- Abstract Classes & Methods
- Interfaces
- Sealed Classes
- Static Classes and Members
- `this` keyword

---

### 🧩 5. **Structs & Enums**

- `struct` vs `class`
- Creating and Using `enum`

---

### 📦 6. **Arrays & Collections**

- 1D Arrays
- 2D Arrays (Rectangular and Jagged)
- `Array` Class Methods
- `List<T>` (in System.Collections.Generic — part of base lib)
- `Dictionary<TKey, TValue>`
- `HashSet<T>`, `Queue<T>`, `Stack<T>`

---

### 🎯 7. **String Manipulation**

- String Methods (`Substring()`, `IndexOf()`, `Replace()`, `Split()`, `ToUpper()`, `Trim()`, etc.)
- String Interpolation (`$"Hello {name}"`)
- `StringBuilder` (from `System.Text`, still standard)
- Escape Characters (`\n`, `\t`, etc.)

---

### 🔐 8. **Exception Handling**

- `try`, `catch`, `finally`
- `throw` keyword
- Custom Exceptions

---

### 📚 9. **Namespaces**

- Declaring & Using Namespaces
- `using` directive
- Nested Namespaces

---

### ⏱️ 10. **Date & Time**

- `DateTime`
- `TimeSpan`
- Formatting Dates and Times
    
    ---
    

### 🧮 11. **Math and Logic**

- `Math` class (`Pow`, `Sqrt`, `Floor`, `Ceiling`, `Abs`, `Max`, `Min`)
- Bitwise Operations
- Random Numbers using `Random`

---

### 🧠 12. **Advanced Concepts**

- Indexers
- Delegates
- Events
- Lambda Expressions
- Anonymous Methods
- Func<> and Action<> (in `System`, part of base)
- Expression-bodied members
- Extension Methods
- Partial Classes and Methods

---

### 💾 13. **File & Directory I/O** _(Optional - still built-in, not external)_

- Reading/Writing Files (`File`, `StreamReader`, `StreamWriter`)
- Directory Management (`Directory`, `Path`)

---

### 🔄 14. **LINQ (Language Integrated Query)**

- `from`, `where`, `select`, `orderby`, etc.
- LINQ to Objects (no external DB)
- `Select()`, `Where()`, `Aggregate()`, `Sum()`, etc.

---

### ⚙️ 15. **Threading & Tasks**

- Basic Threading (`Thread` class)
- `Task` and `async/await`
- `lock`, `Monitor`, `Mutex` for thread safety

---

### 🔍 16. **Reflection**

- Accessing metadata of types at runtime
- Using `Type`, `PropertyInfo`, `MethodInfo`

---

### 🧰 17. **Attributes**

- Using built-in attributes like `[Obsolete]`, `[Serializable]`
- Custom Attributes
- Accessing them via Reflection

---

### 🧪 18. **Unit Testing Logic (Manual)**

- Simulating test cases with assertions using custom logic (no framework)

---

## ✅ Optional Topics That Still Use Built-in Framework:

These are included in .NET and don’t count as “external”:

- `System.Text.RegularExpressions` for Regex
- `System.Diagnostics` for logging or debugging
- `System.Net` for basic web requests (if allowed)
- `System.Xml` or `System.Json` for XML/JSON parsing

