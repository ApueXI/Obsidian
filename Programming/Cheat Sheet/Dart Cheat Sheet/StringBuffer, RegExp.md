---
Created: 2025-09-16T20:29
tags:
  - Dart-Core-Library-(no-external-imports)
---
# 🎯 Dart `StringBuffer` & `RegExp` Cheat Sheet

## 1. StringBuffer

### **Purpose**

- Efficiently **builds strings** by appending multiple parts.
- Avoids creating **many intermediate strings** (better performance than `+` concatenation in loops).

### **Basic Usage**

```Dart
void main() {
  var buffer = StringBuffer();

  buffer.write("Hello");
  buffer.write(" ");
  buffer.write("World!");

  print(buffer.toString()); // Hello World!
}

```

### **Useful Methods**

|Method|Description|
|---|---|
|`.write(Object)`|Append string/object|
|`.writeln(Object)`|Append string + newline|
|`.toString()`|Convert buffer to final string|
|`.clear()`|Clear all contents|

### **Example: Efficient Concatenation**

```Dart
void main() {
  var words = ["Dart", "is", "awesome"];
  var buffer = StringBuffer();

  for (var word in words) {
    buffer.write(word);
    buffer.write(" ");
  }

  print(buffer.toString().trim()); // Dart is awesome
}

```

✅ More memory-efficient than repeatedly using `+`.

---

## 2. RegExp (Regular Expressions)

### **Purpose**

- Used for **pattern matching, searching, replacing, and validating strings**.

### **Basic Usage**

```Dart
void main() {
  var pattern = RegExp(r'\d+'); // matches one or more digits
  var text = "Order 123, Item 456";

  var matches = pattern.allMatches(text);
  for (var match in matches) {
    print(match[0]); // 123, 456
  }
}

```

### **Common Methods**

|Method|Description|
|---|---|
|`hasMatch(String)`|Returns true if pattern matches|
|`stringMatch(String)`|Returns first match as string|
|`allMatches(String)`|Returns iterable of all matches|
|`replaceAll(RegExp, String)`|Replace all matches|
|`split(String)`|Split string by pattern|

### **Example: Validate Email**

```Dart
void main() {
  var emailPattern = RegExp(r'^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$');
  var email = "user@example.com";

  if (emailPattern.hasMatch(email)) {
    print("Valid email");
  } else {
    print("Invalid email");
  }
}

```

✅ `RegExp` is **powerful for string validation and parsing**.

---

## 3. Summary Table

|Class|Purpose|Key Methods|
|---|---|---|
|`StringBuffer`|Efficient string building|`.write()`, `.writeln()`, `.toString()`, `.clear()`|
|`RegExp`|Pattern matching & validation|`hasMatch()`, `allMatches()`, `stringMatch()`, `replaceAll()`|

---

## 4. Real-World Example

💡 **Extract All Numbers from Text and Concatenate**

```Dart
void main() {
  var text = "Order 123, Item 456, ID 789";
  var pattern = RegExp(r'\d+');
  var buffer = StringBuffer();

  for (var match in pattern.allMatches(text)) {
    buffer.write(match[0]);
    buffer.write("-");
  }

  print(buffer.toString().substring(0, buffer.length - 1));
  // 123-456-789
}

```

✅ Combines `RegExp` + `StringBuffer` efficiently.