---
Created: 2025-08-07T20:10
tags:
  - Reflection
---
## ✅ 1. Concepts Explained

### 🔹 `Type` (System.Type)

Represents metadata about a type — class, struct, enum, etc. It’s the entry point for reflection.

```C#
Type t = typeof(MyClass);      // If type is known
Type t = obj.GetType();        // At runtime from instance
```

Use it to get:

- Properties: `t.GetProperties()`
- Methods: `t.GetMethods()`
- Fields: `t.GetFields()`
- Constructors: `t.GetConstructors()`
- Specific members: `t.GetMethod("MyMethod")`, etc.

---

### 🔹 `PropertyInfo` (System.Reflection.PropertyInfo)

Represents metadata for a **property**.

You can:

- Get value: `prop.GetValue(obj)`
- Set value: `prop.SetValue(obj, value)`
- Inspect name, type, etc.

```C#
PropertyInfo prop = t.GetProperty("Name");
prop.SetValue(obj, "Alice");
string name = (string)prop.GetValue(obj);
```

---

### 🔹 `MethodInfo` (System.Reflection.MethodInfo)

Represents metadata for a **method**.

You can:

- Invoke method: `method.Invoke(obj, params)`
- Check parameters, return type, method name, etc.

```C#
MethodInfo method = t.GetMethod("SayHello");
method.Invoke(obj, null);  // Call method on instance
```

---

## 🧾 2. Summary Table

|Concept|Class/Method|Example|
|---|---|---|
|Get Type|`typeof(T)` / `obj.GetType()`|`Type t = typeof(Person);`|
|Get property|`t.GetProperty("PropName")`|`PropertyInfo p = t.GetProperty("Name");`|
|Get method|`t.GetMethod("MethodName")`|`MethodInfo m = t.GetMethod("SayHi");`|
|Get value|`prop.GetValue(obj)`|`prop.GetValue(myObj);`|
|Set value|`prop.SetValue(obj, val)`|`prop.SetValue(myObj, "Test");`|
|Invoke method|`method.Invoke(obj, params[])`|`method.Invoke(myObj, null);`|

---

## 💡 3. Real-World Example

### 👤 Class to Inspect

```C#
public class Person {
    public string Name { get; set; }

    public void Greet() {
        Console.WriteLine($"Hello, my name is {Name}");
    }
}
```

### 🧪 Reflection Code

```C#
Type type = typeof(Person);
object person = Activator.CreateInstance(type);  // new Person()

// Set the 'Name' property
PropertyInfo nameProp = type.GetProperty("Name");
nameProp.SetValue(person, "Alice");

// Get and display the 'Name' property
string name = (string)nameProp.GetValue(person);
Console.WriteLine("Name: " + name);  // Outputs: Name: Alice

// Call the Greet() method
MethodInfo greetMethod = type.GetMethod("Greet");
greetMethod.Invoke(person, null);  // Outputs: Hello, my name is Alice
```

---

## ⚠️ 4. Gotchas

|Pitfall|Explanation|
|---|---|
|❌ Null returns|If property or method name is misspelled or doesn’t exist. Always check for `null`.|
|❌ Boxing/unboxing|When dealing with value types (e.g., `int`, `bool`), remember to cast when using `GetValue`.|
|✅ Use `BindingFlags`|For non-public, static, or instance members.|
|✅ Type safety|Be careful with object casting when using `GetValue` or `Invoke`.|

### Example with BindingFlags:

```C#
PropertyInfo p = t.GetProperty("Name", BindingFlags.Instance | BindingFlags.Public);
```