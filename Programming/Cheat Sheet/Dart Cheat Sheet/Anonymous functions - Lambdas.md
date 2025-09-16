---
Created: 2025-09-16T20:01
tags:
  - Functions
---
# 🎯 Dart Anonymous Functions (Lambdas) Cheat Sheet

## 1. Full Explanation

- **Anonymous functions** (also called **lambdas**) are functions **without a name**.
- They can be assigned to variables, passed as arguments, or used inline (like callbacks).
- Two syntaxes:
    - **Block body:** `(params) { statements; }`
    - **Expression body (arrow):** `(params) => expression;`

✅ Often used in **collections** (`map`, `where`, `forEach`) and **Flutter callbacks**.

---

## 2. Examples

### 🔹 Assigned to a variable

```Dart
void main() {
  var greet = (String name) {
    return "Hello, $name!";
  };

  print(greet("Alice")); // Hello, Alice!
}

```

---

### 🔹 Using Arrow Style

```Dart
void main() {
  var square = (int x) => x * x;

  print(square(4)); // 16
}

```

---

### 🔹 As Callback

```Dart
void main() {
  var numbers = [1, 2, 3];

  numbers.forEach((n) {
    print("Number: $n");
  });
}

```

---

### 🔹 Inline in Flutter Widgets

```Dart
ElevatedButton(
  onPressed: () {
    print("Button Pressed!");
  },
  child: Text("Click Me"),
)

```

---

## 3. Summary Table

|Usage|Syntax|Example|
|---|---|---|
|Block body|`(params) { statements; }`|`(x, y) { return x + y; }`|
|Expression body|`(params) => expression`|`(n) => n * 2`|
|Variable|`var f = (x) => x*x;`|`f(5); // 25`|
|Callback|`list.forEach((n){print(n);});`|`forEach` with inline lambda|

---

## 4. Real-World Example

💡 **Filtering and Mapping with Lambdas**

```Dart
void main() {
  var numbers = [1, 2, 3, 4, 5, 6];

  // Filter even numbers and double them
  var result = numbers
      .where((n) => n % 2 == 0)   // filter even
      .map((n) => n * 2)          // double values
      .toList();

  print(result); // [4, 8, 12]
}

```

✅ Cleaner and more readable than writing named functions.