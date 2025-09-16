---
Created: 2025-06-25T17:24
---
### **What Is JSON?**

- **JSON** stands for **JavaScript Object Notation**
- It's a **lightweight data format** used to exchange data between systems (often between frontend and backend)
- Syntax is **key-value pairs** like JavaScript objects, but:
    - All keys must be in **double quotes**
    - No comments allowed

```JSON
{
  "name": "Alice",
  "age": 25,
  "isMember": true}
{
```

  

### **Convert JS Object ↔ JSON**

### ✅ Object → JSON string

```JavaScript
const obj = { name: "Alice", age: 25 };
const jsonStr = JSON.stringify(obj);
console.log(jsonStr); // '{"name":"Alice","age":25}'
```

### ✅ JSON string → Object

```JavaScript
const jsonStr = '{"name":"Alice","age":25}';
const obj = JSON.parse(jsonStr);
console.log(obj.name); // "Alice"
```

  

### **Using JSON from a File (Browser)**

You can fetch a JSON file from a server or local project:

### ✅ `data.json`

```JSON
{
  "title": "Hello",
  "count": 3
}
```

### ✅ JavaScript

```JavaScript
fetch("data.json")
  .then(res => res.json())
  .then(data => {
    console.log(data.title); // "Hello"
  })
  .catch(err => console.error("Fetch error:", err));
```

  

### **Use** `**JSON.stringify**` **Options**

```JavaScript
const user = { name: "Bob", age: 30 };

const pretty = JSON.stringify(user, null, 2); // Indented output
console.log(pretty);
```

```JSON
{
  "name": "Bob",
  "age": 30
}
```

  

### **Store/Read JSON in LocalStorage**

```JavaScript
const settings = { theme: "dark" };

// Save to localStorage
localStorage.setItem("settings", JSON.stringify(settings));

// Read from localStorage
const saved = JSON.parse(localStorage.getItem("settings"));
console.log(saved.theme); // "dark"
```

  

### **Invalid JSON Examples (Don't Do These)**

```JavaScript
// ❌ Missing double quotes around keys
{ name: "Alice" }

// ❌ Trailing comma
{ "name": "Alice", }

// ❌ Comment
{ "name": "Alice" // comment }
```

  

### Summary Table

|   |   |
|---|---|
|Task|Method|
|Object → JSON string|`JSON.stringify(obj)`|
|JSON string → Object|`JSON.parse(jsonString)`|
|Fetch from file/server|`fetch("file.json")`|
|Store in localStorage|Use `JSON.stringify` to save|
|Read from localStorage|Use `JSON.parse` to read|

  

```JavaScript
const names = ["Acob", "Goco", "Andy", "Zam"];

const person = {
    name: "Acob",
    age: "19",
    isStudent: true,
    hobbies: ["gambling", "playing", "reading"],
};

const people = [
    {
        name: "Acob",
        age: 19,
        isStudent: true,
    },
    {
        name: "Andy",
        age: 16,
        isStudent: false,
    },
    {
        name: "Goco",
        age: 25,
        isStudent: false,
    },
    {
        name: "Zam",
        age: 21,
        isStudent: true,
    },
];

const jsonNames = JSON.stringify(names);
const jsonPerson = JSON.stringify(person);
const jsonPeople = JSON.stringify(people);

console.log(names);
console.log(jsonNames);
console.log(person);
console.log(jsonPerson);
console.log(people);
console.log(jsonPeople);
```

  

```JavaScript
const jsonnames = `["Acob", "Goco", "Andy", "Zam"]`;

const jsonperson = `{ "name": "Acob", "age": "19", "isStudent": true, "hobbies": ["gambling", "playing", "reading"] }`;

const jsonpeople = `[ { "name": "Acob", "age": 19, "isStudent": true }, { "name": "Andy", "age": 16, "isStudent": false }, { "name": "Goco", "age": 25, "isStudent": false }, { "name": "Zam", "age": 21, "isStudent": true } ]`;

const parseName = JSON.parse(jsonnames);
const parsePerson = JSON.parse(jsonperson);
const parsePeople = JSON.parse(jsonpeople);

console.log(jsonnames);
console.log(parseName);
console.log(jsonperson);
console.log(parsePerson);
console.log(jsonpeople);
console.log(parsePeople);
```

  

```JavaScript
fetch("../JSONPeople.json")
    .then((response) => {
        return response.json();
    })
    .then((value) => {
        value.forEach((value) => {
            console.log(value);
            console.log(value.name);
            console.log(value.age);
        });
    })
    .catch((error) => {
        console.log(`Error: ${error}`);
    });
```