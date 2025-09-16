---
Created: 2025-06-20T15:14
---
### **Creating an Object**

```JavaScript
const person = {
  name: "Alice",
  age: 25,
  isStudent: true
};
```

- **Explanation:** An object is a collection of key-value pairs (also called properties).

  

### **Accessing Properties**

```JavaScript
console.log(person.name);       // Dot notation
console.log(person["age"]);     // Bracket notation
```

- Use `.` for simple keys, `[]` when key is stored in a variable or includes special characters.

  

### **Modifying Properties**

```JavaScript
person.age = 26;
person["isStudent"] = false;
```

- You can update existing values using either notation.

  

### **Adding New Properties**

```JavaScript
person.city = "Manila";
```

- Add new key-value pairs dynamically.

  

### **Deleting Properties**

```JavaScript
delete person.isStudent;
```

- Removes the property from the object.

  

### **Methods (Functions in Objects)**

```JavaScript
const user = {
  name: "Bob",
  greet() {
    return `Hello, I'm ${this.name}`;
  }
};

console.log(user.greet());
```

- **Explanation:** Functions inside objects are called **methods**. Use `this` to refer to the object.

  

### **Object Destructuring**

```JavaScript
const { name, age } = person;
console.log(name, age);
```

- **Explanation:** Extract values into variables quickly.

  

### **Computed Property Names**

```JavaScript
const key = "score";
const student = {
  [key]: 95
};
console.log(student.score); // 95
```

- Useful when keys need to be dynamic.

  

### **Object Shorthand**

```JavaScript
const x = 10;
const y = 20;
const point = { x, y };
```

- If variable name and property name are the same, you can skip `x: x`.

  

### **Looping Through Objects**

```JavaScript
for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}
```

- Loops through all enumerable properties (keys).

  

### Bonus: `Object.keys`, `Object.values`, `Object.entries`

```JavaScript
Object.keys(person);   // ['name', 'age', 'city']
Object.values(person); // ['Alice', 26, 'Manila']
Object.entries(person); // [['name', 'Alice'], ['age', 26], ['city', 'Manila']]
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Syntax / Example|Notes|
|Create object|`const obj = { key: value }`|Basic object|
|Access|`obj.key` or `obj["key"]`|Use `[]` if key is dynamic or special|
|Add/Update|`obj.newKey = value`|Adds or changes property|
|Delete|`delete obj.key`|Removes a property|
|Method|`greet() { return this.name; }`|Function inside object|
|Destructure|`const { a, b } = obj`|Extracts values|
|Loop|`for (let k in obj)`|Loops through keys|

  

```JavaScript
const person = {
    firstname: "Laren",
    lastneme: "Acob",
    age: 30,
    isEmployed: true,
    sayHello: () => console.log(`Hello`),
    sayEat: function () {
        console.log(`Im eating a fish`);
    },
    greet() {
        return `Hello world`;
    },
};

console.log(person.firstname);
person.sayHello();
person.sayEat();
console.log(person.greet());
```