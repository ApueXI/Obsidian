---
Created: 2025-08-07T20:10
tags:
  - Reflection
---
## ✅ 1. Concept Overview

**Reflection** allows you to inspect **types, properties, methods, fields, attributes**, etc., at **runtime** — even if you don't know the type at compile time.

You can:

- Load assemblies dynamically
- Inspect types
- Create instances
- Invoke methods
- Get/set fields and properties
- Read custom attributes

Namespace:

```C#
using System.Reflection;
```

---

## 🧩 Common Use Cases

- Dependency Injection Containers
- Object Mappers (e.g., AutoMapper)
- Serialization frameworks (e.g., JSON.NET)
- Testing & mocking
- Plugin systems

---

## 🧾 2. Summary Table

|**Action**|**Method / API**|**Example**|
|---|---|---|
|Get Type|`typeof(MyClass)` / `obj.GetType()`|`typeof(string)` or `"hello".GetType()`|
|Get all properties|`type.GetProperties()`|`typeof(MyClass).GetProperties()`|
|Get all fields|`type.GetFields()`|`typeof(MyClass).GetFields()`|
|Get all methods|`type.GetMethods()`|`typeof(MyClass).GetMethods()`|
|Get all constructors|`type.GetConstructors()`|`typeof(MyClass).GetConstructors()`|
|Get a specific member|`type.GetMethod("MethodName")`|`typeof(MyClass).GetMethod("PrintName")`|
|Create an instance|`Activator.CreateInstance(type)`|`Activator.CreateInstance(typeof(MyClass))`|
|Invoke a method|`methodInfo.Invoke(obj, params)`|`methodInfo.Invoke(myObj, new object[] { "Hello" })`|
|Access a property|`propertyInfo.GetValue(obj)` / `.SetValue()`|`propInfo.GetValue(myObj)` or `propInfo.SetValue(myObj, "NewValue")`|
|Read attributes|`type.GetCustomAttributes(...)`|`typeof(MyClass).GetCustomAttributes(false)` or `memberInfo.GetCustomAttributes(true)`|

---

## 🔧 3. Key Classes and Methods

### 🔹 `Type`

Represents metadata about a class, interface, enum, etc.

```C#
Type t = typeof(MyClass);           // Known at compile time
Type t = obj.GetType();             // Runtime object
```

### 🔹 Getting Members

```C#
MethodInfo method = t.GetMethod("MyMethod");
PropertyInfo prop = t.GetProperty("MyProp");
FieldInfo field = t.GetField("myField");
ConstructorInfo ctor = t.GetConstructor(Type.EmptyTypes);
```

### 🔹 Creating Objects Dynamically

```C#
object obj = Activator.CreateInstance(t);
```

### 🔹 Invoking Members

```C#
method.Invoke(obj, new object[] { param1, param2 });
prop.SetValue(obj, value);
object val = prop.GetValue(obj);
```

### 🔹 Reading Custom Attributes

```C#
var attrs = t.GetCustomAttributes(typeof(MyAttribute), inherit: true);
```

---

## 💡 4. Real-World Example

Let’s say you want to inspect and call a method from an unknown class at runtime:

### Example Class:

```C#
public class Person {
    public string Name { get; set; }
    public void SayHello() {
        Console.WriteLine($"Hi, I’m {Name}");
    }
}
```

### Using Reflection:

```C#
Type type = typeof(Person);
object personInstance = Activator.CreateInstance(type);

PropertyInfo nameProp = type.GetProperty("Name");
nameProp.SetValue(personInstance, "Alice");

MethodInfo sayHello = type.GetMethod("SayHello");
sayHello.Invoke(personInstance, null);
```

🧠 Output:

```Plain
Hi, I’m Alice
```

---

## ⚠️ 5. Gotchas & Best Practices

|Caution|Explanation|
|---|---|
|❌ Performance|Reflection is slower than direct calls. Cache `MethodInfo` or `PropertyInfo` if possible.|
|❌ Exception-prone|Misspelling member names causes `null` or `MissingMethodException`.|
|✅ Use `BindingFlags`|To access `private`, `static`, or non-public members.|
|✅ Prefer expression trees or delegates|For better performance in advanced scenarios.|

### Example with `BindingFlags`:

```C#
var privateField = type.GetField("_secret", BindingFlags.NonPublic | BindingFlags.Instance);
```