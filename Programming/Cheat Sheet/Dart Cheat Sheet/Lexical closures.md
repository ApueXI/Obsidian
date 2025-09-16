---
Created: 2025-09-16T20:02
tags:
  - Functions
---
# 🎯 Dart Lexical Closures Cheat Sheet

## 1. Full Explanation

- A **closure** is a function that **captures variables from its lexical scope** (the environment where it was created).
- Even after the outer function has finished executing, the closure keeps access to those variables.
- This is possible because Dart functions are **lexically scoped** → they "remember" the context they were created in.
- ✅ Useful for callbacks, factories, and maintaining state without classes.

---

## 2. Examples

### 🔹 Basic Closure Capturing a Variable

```Dart
Function makeCounter() {
  int count = 0; // captured variable

  return () {
    count++; // closure modifies outer variable
    return count;
  };
}

void main() {
  var counter = makeCounter();

  print(counter()); // 1
  print(counter()); // 2
  print(counter()); // 3
}

```

➡️ The closure "remembers" `count` across calls, even though `makeCounter()` has finished.

---

### 🔹 Closure with Parameters

```Dart
Function multiplier(int factor) {
  return (int x) => x * factor;
}

void main() {
  var doubleIt = multiplier(2);
  var tripleIt = multiplier(3);

  print(doubleIt(5)); // 10
  print(tripleIt(5)); // 15
}

```

---

### 🔹 Using Closures in Loops

```Dart
void main() {
  var functions = <Function>[];

  for (var i = 1; i <= 3; i++) {
    functions.add(() => print("Captured i: $i"));
  }

  functions.forEach((f) => f());
}

```

✅ Each closure captures its own `i`, printing:

```Plain
Captured i: 1
Captured i: 2
Captured i: 3

```

---

### 🔹 Flutter Example

```Dart
List<Widget> makeButtons(List<String> labels) {
  return labels.map((label) {
    return ElevatedButton(
      onPressed: () => print("You clicked $label"),
      child: Text(label),
    );
  }).toList();
}

```

➡️ Each button’s callback closure **captures its own** `**label**`.

---

## 3. Summary Table

|Concept|Example|What Happens|
|---|---|---|
|Capture variable|`makeCounter()`|Closure keeps `count` alive|
|Return function|`multiplier(2)`|Function remembers `factor`|
|Loop capture|`( ) => print(i)`|Each closure remembers its own `i`|
|Flutter UI|`onPressed: ()=>print(label)`|Each button remembers its label|

---

## 4. Real-World Example

💡 **Event Handlers with Closures**

```Dart
typedef ClickHandler = void Function();

List<ClickHandler> makeHandlers(List<String> names) {
  return names.map((name) {
    return () => print("Hello, $name!");
  }).toList();
}

void main() {
  var handlers = makeHandlers(["Alice", "Bob", "Charlie"]);

  handlers[0](); // Hello, Alice!
  handlers[1](); // Hello, Bob!
  handlers[2](); // Hello, Charlie!
}

```

✅ Each handler closure "remembers" the correct `name`.