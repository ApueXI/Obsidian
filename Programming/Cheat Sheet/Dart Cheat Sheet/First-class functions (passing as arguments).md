---
Created: 2025-09-16T20:02
tags:
  - Functions
---
# 🎯 Dart First-Class Functions Cheat Sheet

## 1. Full Explanation

- In Dart, **functions are first-class citizens**, meaning:
    - You can **assign them to variables**
    - You can **pass them as arguments** to other functions
    - You can **return them from other functions**
- This makes Dart flexible for **callbacks, higher-order functions, and functional programming**.

---

## 2. Examples

### 🔹 Assigning a Function to a Variable

```Dart
String greet(String name) => "Hello, $name!";

void main() {
  var sayHello = greet;  // assign function
  print(sayHello("Alice")); // Hello, Alice!
}

```

---

### 🔹 Passing a Function as an Argument

```Dart
void printMessage(String msg) {
  print("Message: $msg");
}

void execute(Function callback) {
  callback("This is Dart!");
}

void main() {
  execute(printMessage); // Message: This is Dart!
}

```

---

### 🔹 Using Arrow Functions as Arguments

```Dart
void execute(Function callback) {
  callback("Hello from callback!");
}

void main() {
  execute((msg) => print(msg)); // Hello from callback!
}

```

---

### 🔹 Returning a Function from Another Function

```Dart
Function multiplier(int factor) {
  return (int x) => x * factor; // returns a lambda
}

void main() {
  var doubleIt = multiplier(2);
  var tripleIt = multiplier(3);

  print(doubleIt(5)); // 10
  print(tripleIt(5)); // 15
}

```

---

### 🔹 Flutter Example

```Dart
ElevatedButton(
  onPressed: () => print("Button clicked"),
  child: Text("Click Me"),
)

```

Here, `onPressed` expects a **function** — we pass a **lambda**.

---

## 3. Summary Table

|Feature|Example|Notes|
|---|---|---|
|Assign function|`var f = greet; f("Bob");`|Function behaves like a variable|
|Pass function|`execute(printMessage);`|Functions as arguments|
|Inline function|`execute((x) => print(x));`|Lambdas as parameters|
|Return function|`multiplier(2)(5); // 10`|Higher-order function|

---

## 4. Real-World Example

💡 **Custom List Filtering with Function Arguments**

```Dart
List<int> filterList(List<int> list, bool Function(int) condition) {
  return list.where(condition).toList();
}

void main() {
  var numbers = [1, 2, 3, 4, 5, 6];

  var evens = filterList(numbers, (n) => n % 2 == 0);
  var greaterThan3 = filterList(numbers, (n) => n > 3);

  print(evens);       // [2, 4, 6]
  print(greaterThan3); // [4, 5, 6]
}

```

✅ Cleaner, reusable, and flexible because **the condition is passed as a function**.