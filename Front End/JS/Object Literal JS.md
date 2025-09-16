---
Created: 2025-06-22T06:35
---
### **What Is an Object Literal?**

An **object literal** is a way to define objects using `{ key: value }` syntax.

```JavaScript
const person = {
  name: "Alice",
  age: 25,
  isStudent: true
};
```

- `{}` creates the object.
- Keys (properties) map to values (data or functions).

  

### **Accessing and Updating Properties**

```JavaScript
console.log(person.name);       // "Alice" - dot notation
console.log(person["age"]);     // 25 - bracket notation

person.age = 26;
person["isStudent"] = false;
```

- Dot `.` is cleaner; bracket `[]` supports dynamic keys.

  

### **Adding and Deleting Properties**

```JavaScript
person.country = "Philippines";
delete person.isStudent;
```

- Add or remove keys anytime.

  

### **Shorthand Property Names**

```JavaScript
const name = "Bob";
const age = 30;

const user = { name, age };
console.log(user); // { name: "Bob", age: 30 }
```

- If key and variable name match, you can omit `key: value`.

  

### **Shorthand Method Definitions**

```JavaScript
const user = {
  name: "Dana",
  greet() {
    return `Hi, I'm ${this.name}`;
  }
};
```

- Cleaner than `greet: function() { ... }`

  

### **Computed Property Names**

```JavaScript
const key = "score";
const player = {
  [key]: 100
};

console.log(player.score); // 100
```

- Use square brackets `[]` to make dynamic property names.

  

### **Nested Objects**

```JavaScript
const student = {
  name: "Ella",
  grades: {
    math: 95,
    science: 90
  }
};

console.log(student.grades.math); // 95
```

- Access inner values with dot chaining.

  

### **Using Functions to Return Object Literals**

```JavaScript
function createUser(name, age) {
  return {
    name,
    age,
    greet() {
      return `Hello, ${this.name}`;
    }
  };
}
```

- Useful for factories or reusable object templates.

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Example|Notes|
|Basic object|`{ key: value }`|Standard object format|
|Shorthand properties|`{ name, age }`|Key = variable name|
|Shorthand methods|`greet() {}`|Clean method definition|
|Computed keys|`{ [key]: value }`|Dynamic property names|
|Access/modify props|`obj.key` / `obj["key"]`|Bracket allows dynamic strings|
|Add/remove|`obj.new = val` / `delete obj.key`|Modify at runtime|
|Nested object|`obj.inner.key`|Access deeply nested data|