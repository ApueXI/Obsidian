---
Created: 2025-08-07T20:10
tags:
  - Attributes
---
  

## ✅ 1. Concept Overview

**Custom attributes** in C# let you define your own metadata and attach it to types, members, parameters, etc.

You can:

- Annotate classes, methods, etc., with your own logic
- Access your custom metadata using **Reflection**
- Use them for validation, configuration, code generation, etc.

---

## 📐 2. Declaring a Custom Attribute

### 🔹 Step 1: Create the Attribute Class

- Inherit from `System.Attribute`
- Use `[AttributeUsage(...)]` to control where the attribute can be applied

```C#
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Method, AllowMultiple = false)]
public class AuthorAttribute : Attribute {
    public string Name { get; }
    public string Date { get; set; }

    public AuthorAttribute(string name) {
        Name = name;
    }
}
```

---

## 🧾 3. Applying a Custom Attribute

```C#
[Author("Nein", Date = "2025-08-06")]
public class MyComponent {
    [Author("AnotherDev")]
    public void Process() {
        // ...
    }
}
```

---

## 🔍 4. Reading Custom Attributes via Reflection

You can retrieve custom attributes using the `MemberInfo.GetCustomAttributes()` method.

```C#
Type type = typeof(MyComponent);
object[] attrs = type.GetCustomAttributes(typeof(AuthorAttribute), inherit: true);

foreach (AuthorAttribute attr in attrs) {
    Console.WriteLine($"Author: {attr.Name}, Date: {attr.Date}");
}
```

---

## 📋 5. Summary Table

|Feature|Syntax / API|Description|
|---|---|---|
|Create custom attribute|`class MyAttr : Attribute { ... }`|Inherit from `System.Attribute`|
|Control usage|`[AttributeUsage(...)]`|Limits where it can be applied|
|Apply attribute|`[MyAttr(...)]`|Attach to class, method, etc.|
|Get attribute via reflection|`type.GetCustomAttributes()`|Returns all applied attributes|
|Access attribute members|`attr.PropertyName`|Access property values like `Name`, `Date`|

---

## 💡 6. Real-World Example

### 🔨 Step 1: Define a Validation Attribute

```C#
[AttributeUsage(AttributeTargets.Property)]
public class NotEmptyAttribute : Attribute {}
```

### 🔧 Step 2: Apply to a Model

```C#
public class User {
    [NotEmpty]
    public string Username { get; set; }

    public int Age { get; set; }
}
```

### 🧪 Step 3: Check Validation with Reflection

```C#
public static void Validate(object obj) {
    Type type = obj.GetType();
    foreach (var prop in type.GetProperties()) {
        var notEmptyAttr = prop.GetCustomAttribute<NotEmptyAttribute>();
        if (notEmptyAttr != null) {
            string value = prop.GetValue(obj) as string;
            if (string.IsNullOrWhiteSpace(value)) {
                Console.WriteLine($"Validation failed: {prop.Name} cannot be empty.");
            }
        }
    }
}
```

### 👇 Usage:

```C#
User u = new User { Username = "", Age = 25 };
Validate(u);  // Output: Validation failed: Username cannot be empty.
```

---

## ⚠️ 7. Gotchas & Best Practices

|Tip|Explanation|
|---|---|
|Always use `[AttributeUsage]`|It avoids unintended use (e.g., on fields instead of methods)|
|Keep custom attribute logic simple|Attributes are **metadata only** — don’t include behavior inside them|
|Combine with Reflection or AOP|Attributes are powerful when paired with tools like validation engines, filters, or source generators|
|Don’t overuse attributes|Too many custom attributes can clutter code and make logic harder to trace|