---
Created: 2025-08-07T20:10
tags:
  - Optional
---
## ✅ 1. XML Parsing with `System.Xml`

### 🔹 Key classes:

- `XmlDocument`: DOM-based XML parsing and manipulation
- `XmlReader`: Forward-only, fast, low-memory parsing
- `XmlSerializer`: Serialize/deserialize objects to/from XML

---

### 🔧 Basic XML Reading with `XmlDocument`

```C#
using System.Xml;

XmlDocument doc = new XmlDocument();
doc.Load("file.xml");

XmlNodeList nodes = doc.SelectNodes("//book/title");
foreach (XmlNode node in nodes) {
    Console.WriteLine(node.InnerText);
}
```

---

### 🔧 XML Reading with `XmlReader` (streaming)

```C#
using System.Xml;

using XmlReader reader = XmlReader.Create("file.xml");
while (reader.Read()) {
    if (reader.NodeType == XmlNodeType.Element && reader.Name == "title") {
        string title = reader.ReadElementContentAsString();
        Console.WriteLine(title);
    }
}
```

---

### 🔧 XML Serialization/Deserialization with `XmlSerializer`

```C#
using System.Xml.Serialization;
using System.IO;

public class Book {
    public string Title { get; set; }
    public string Author { get; set; }
}

XmlSerializer serializer = new XmlSerializer(typeof(Book));

// Deserialize from XML string
using StringReader reader = new StringReader(xmlString);
Book book = (Book)serializer.Deserialize(reader);

// Serialize to XML string
using StringWriter writer = new StringWriter();
serializer.Serialize(writer, book);
string xmlOutput = writer.ToString();
```

---

## ✅ 2. JSON Parsing with `System.Text.Json`

### 🔹 Key classes:

- `JsonSerializer`: Serialize/deserialize objects
- `JsonDocument`: Read-only DOM for JSON data
- `Utf8JsonReader`: Forward-only JSON reader for high performance

---

### 🔧 Deserialize JSON to Object

```C#
using System.Text.Json;

public class User {
    public string Name { get; set; }
    public int Age { get; set; }
}

string jsonString = "{\"Name\":\"Alice\",\"Age\":30}";
User user = JsonSerializer.Deserialize<User>(jsonString);
Console.WriteLine(user.Name);  // Outputs: Alice
```

---

### 🔧 Serialize Object to JSON

```C#
User user = new User { Name = "Bob", Age = 25 };
string json = JsonSerializer.Serialize(user);
Console.WriteLine(json); // {"Name":"Bob","Age":25}
```

---

### 🔧 Reading JSON with `JsonDocument`

```C#
using System.Text.Json;

string jsonString = "{\"Name\":\"Alice\",\"Age\":30}";
using JsonDocument doc = JsonDocument.Parse(jsonString);
JsonElement root = doc.RootElement;

string name = root.GetProperty("Name").GetString();
int age = root.GetProperty("Age").GetInt32();

Console.WriteLine($"{name} is {age} years old.");
```

---

## 🧾 3. Summary Table

|Feature|XML (`System.Xml`)|JSON (`System.Text.Json`)|
|---|---|---|
|Parse full document|`XmlDocument.Load()`|`JsonDocument.Parse()`|
|Stream parsing|`XmlReader`|`Utf8JsonReader`|
|Serialize / Deserialize|`XmlSerializer`|`JsonSerializer`|
|Access elements/properties|`XmlNode`, `XmlElement`|`JsonElement`|

---

## ⚠️ 4. Gotchas & Tips

|Tip|Explanation|
|---|---|
|For XML, prefer `XmlReader` for large files|Streaming parsing uses less memory|
|Use `[XmlElement]`, `[XmlAttribute]` for mapping|Controls XML serialization details|
|`System.Text.Json` is faster than `Newtonsoft.Json` but less feature-rich|For advanced needs, consider `Newtonsoft.Json`|
|Use `JsonSerializerOptions` to control casing, ignore nulls, etc.|Customize JSON behavior|