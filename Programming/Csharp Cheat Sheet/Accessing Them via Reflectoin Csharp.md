---
Created: 2025-08-07T20:10
tags:
  - Attributes
---
## ✅ 1. What Is This?

Once you decorate classes, properties, or methods with **custom attributes**, you can use **Reflection** at runtime to **read those attributes and their values**.

This is useful for:

- Custom validation
- Generating documentation
- Plugin systems
- Dynamic behavior (e.g., feature toggles)

---

## 📦 2. Key APIs for Reading Attributes

|Member Type|API|Description|
|---|---|---|
|Class|`Type.GetCustomAttributes()`|Get all attributes applied to a class|
|Property|`PropertyInfo.GetCustomAttributes()`|Get all attributes applied to a property|
|Method|`MethodInfo.GetCustomAttributes()`|Get all attributes applied to a method|
|Specific type|`.GetCustomAttribute<T>()` or `.OfType<T>()`|Strongly-typed access|
|Check if exists|`.IsDefined(typeof(MyAttribute), true)`|Boolean check|

---

## 🔧 3. Accessing Custom Attributes – Step-by-Step

### 🧩 Given This Custom Attribute:

```C#
[AttributeUsage(AttributeTargets.All)]
public class AuthorAttribute : Attribute {
    public string Name { get; }
    public string Date { get; set; }

    public AuthorAttribute(string name) {
        Name = name;
    }
}
```

---

### 👤 Applied to a Class & Method:

```C#
[Author("Nein", Date = "2025-08-06")]
public class MyClass {
    [Author("Charlie")]
    public void DoWork() {}
}
```

---

### 🔍 Use Reflection to Access:

### 🔹 Class-Level Attribute

```C#
Type type = typeof(MyClass);

var classAttrs = type.GetCustomAttributes(typeof(AuthorAttribute), inherit: true);
foreach (AuthorAttribute attr in classAttrs) {
    Console.WriteLine($"[Class] Author: {attr.Name}, Date: {attr.Date}");
}
```

### 🔹 Method-Level Attribute

```C#
MethodInfo method = type.GetMethod("DoWork");

var methodAttrs = method.GetCustomAttributes(typeof(AuthorAttribute), inherit: true);
foreach (AuthorAttribute attr in methodAttrs) {
    Console.WriteLine($"[Method] Author: {attr.Name}, Date: {attr.Date}");
}
```

### 🔹 Using Generic Version (Cleaner)

```C#
AuthorAttribute attr = method.GetCustomAttribute<AuthorAttribute>();
Console.WriteLine(attr.Name);  // Output: Charlie
```

---

## 💡 4. Real-World Example: Auto-Logging Attributes

### Define Attribute

```C#
[AttributeUsage(AttributeTargets.Method)]
public class LogAttribute : Attribute {
    public string Message { get; }
    public LogAttribute(string message) => Message = message;
}
```

### Apply It

```C#
public class Actions {
    [Log("Starting calculation")]
    public void Calculate() {
        // ...
    }
}
```

### Detect via Reflection

```C#
Type type = typeof(Actions);
MethodInfo[] methods = type.GetMethods();

foreach (var m in methods) {
    var logAttr = m.GetCustomAttribute<LogAttribute>();
    if (logAttr != null) {
        Console.WriteLine($"Log: {logAttr.Message} before calling {m.Name}");
        m.Invoke(Activator.CreateInstance(type), null);
    }
}
```

---

## 🧾 5. Summary Table

|Use Case|Code Example|
|---|---|
|Get all class attributes|`type.GetCustomAttributes()`|
|Get specific attr|`type.GetCustomAttribute<MyAttr>()`|
|Method attributes|`methodInfo.GetCustomAttributes()`|
|Property attributes|`propertyInfo.GetCustomAttributes()`|
|Check if attr is defined|`type.IsDefined(typeof(MyAttr), true)`|

---

## ⚠️ Gotchas & Tips

|Tip|Why|
|---|---|
|Always check for `null` when using `.GetCustomAttribute<T>()`|The attribute might not be applied|
|Use `inherit: true` if dealing with inherited attributes|Some custom attributes may be inherited|
|Use LINQ with `.OfType<T>()`|Easy filtering from `object[]` returned by `.GetCustomAttributes()`|
|Cache reflection results|Improves performance, especially in loops or large assemblies|