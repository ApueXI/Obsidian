---
Created: 2025-08-07T20:10
tags:
  - Namespaces
---
## 1️⃣ Using Directive for Namespaces

- Allows **importing namespaces** to access types without full qualification.

```C#
using System.Text;

class Program
{
    static void Main()
    {
        StringBuilder sb = new StringBuilder();  // No need to write System.Text.StringBuilder
    }
}
```

- Place all `using` directives at the **top of your C# files**.
- Can include multiple namespaces:

```C#
using System;
using System.Collections.Generic;
```

---

## 2️⃣ Using Alias Directive

- Create **aliases** for namespaces or types to avoid conflicts or simplify usage.

```C#
using Proj1 = MyCompany.Project.Module1;
using Proj2 = MyCompany.Project.Module2;

Proj1.MyClass obj1 = new Proj1.MyClass();
Proj2.MyClass obj2 = new Proj2.MyClass();
```

- Aliases can also be for types:

```C#
using TextBuilder = System.Text.StringBuilder;
TextBuilder sb = new TextBuilder();
```

---

## 3️⃣ `using` Statement (Resource Management) — Different from `using` Directive

- Not to be confused with the `using` **directive** above.
- The `using` **statement** helps with **automatic disposal** of resources implementing `IDisposable`.

```C#
using (var file = new StreamReader("file.txt"))
{
    string content = file.ReadToEnd();
}
// file.Dispose() is called automatically here
```

- In C# 8+, you can use `**using**` **declaration** syntax:

```C#
using var file = new StreamReader("file.txt");
string content = file.ReadToEnd();
// file.Dispose() called at end of scope
```

---

## 📋 Summary Table

|Purpose|Syntax/Example|Notes|
|---|---|---|
|Import namespaces|`using System.Collections.Generic;`|Access types without full name|
|Alias namespaces|`using Proj = MyCompany.Project.Module;`|Shorten or disambiguate names|
|Alias types|`using SB = System.Text.StringBuilder;`|Shorter type name|
|Resource management|`using (var r = new Resource()) { ... }`|Dispose after use|
|Resource declaration|`using var r = new Resource();`|Dispose at scope end (C# 8+)|

---

## 🧪 Real-World Example

```C#
using System;
using TextBuilder = System.Text.StringBuilder;

class Program
{
    static void Main()
    {
        TextBuilder sb = new TextBuilder();
        sb.Append("Hello, ");
        sb.Append("World!");
        Console.WriteLine(sb.ToString());
    }
}
```