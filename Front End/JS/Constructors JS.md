---
Created: 2025-06-20T15:53
---
### **What is a Constructor?**

A **constructor** is a special function used to **create and initialize objects**.

  

### **Basic Constructor Function**

```JavaScript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const alice = new Person("Alice", 25);
console.log(alice.name); // "Alice"
```

- `this.name` → property of the object being created.
- `new Person(...)` creates a new object and sets `this` to that object.

  

### **Using Methods in Constructors**

```JavaScript
function Dog(name) {
  this.name = name;
  this.bark = function () {
    return `${this.name} says woof!`;
  };
}

const dog = new Dog("Max");
console.log(dog.bark()); // "Max says woof!"
```

- Methods can be defined directly inside the constructor, but this **duplicates the method for each instance**.

  

### **Prototype Methods (More Efficient)**

```JavaScript
function Car(model) {
  this.model = model;
}

Car.prototype.drive = function () {
  return `${this.model} is driving.`;
};

const myCar = new Car("Toyota");
console.log(myCar.drive()); // "Toyota is driving."
```

- Defining methods on `.prototype` **shares the method across all instances**, saving memory.

  

### **Constructor with** `**new**` **Keyword**

```JavaScript
const user = new Person("Jane", 30);
```

Using `new`:

1. Creates a blank object
2. Sets `this` to that object
3. Runs the constructor code
4. Returns the object

  

### **ES6 Class Syntax (Alternative to Constructor Functions)**

```JavaScript
class Student {
  constructor(name, grade) {
    this.name = name;
    this.grade = grade;
  }

  introduce() {
    return `Hi, I'm ${this.name} in grade ${this.grade}.`;
  }
}

const s1 = new Student("Ella", 6);
console.log(s1.introduce());
```

- `class` is **just syntax sugar** over constructor functions and prototypes.

  

### **Custom** `**this**` **Behavior (with** `**call**`**)**

```JavaScript
function Animal(type) {
  this.type = type;
}

const cat = {};
Animal.call(cat, "Cat");

console.log(cat.type); // "Cat"
```

- You can **reuse a constructor on another object** using `.call()` or `.apply()`.

  

### Summary Table

|   |   |
|---|---|
|Feature|Description|
|`function Name(...)`|Defines a constructor function|
|`new Name(...)`|Creates a new object using the constructor|
|`this.property = value`|Sets property on the new object|
|`.prototype.method`|Shares methods across all instances|
|`class` syntax|Cleaner way to define constructors + methods|

  

```JavaScript
function Car(make, model, year, color) {
    this.make = make;
    this.model = model;
    this.year = year;
    this.color = color;
    this.drive = function () {
        console.log(`You dirve the ${this.model}`);
    };
}

const car1 = new Car("Ford", "Mustang", 2024, "red");
const car2 = new Car("Chevrolet", "Camaro", 2025, "blue");

console.log(car1);
console.log(car2);
car1.drive();
car2.drive();
```