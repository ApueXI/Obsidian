---
Created: 2025-06-20T16:09
---
### **Basic Class Declaration**

```JavaScript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    return `Hi, I'm ${this.name}.`;
  }
}

const p1 = new Person("Alice", 25);
console.log(p1.greet()); // "Hi, I'm Alice."
```

- `class` keyword defines a blueprint.
- `constructor` runs when an object is created.
- Methods go **outside** the constructor.

  

### **Class Expression (Anonymous or Named)**

```JavaScript
const Animal = class {
  constructor(type) {
    this.type = type;
  }

  speak() {
    return `${this.type} makes a sound.`;
  }
};

const cat = new Animal("Cat");
console.log(cat.speak());
```

- Class expressions can be assigned to variables.

  

### **Adding Methods**

```JavaScript
class Circle {
  constructor(radius) {
    this.radius = radius;
  }

  area() {
    return Math.PI * this.radius ** 2;
  }

  static describe() {
    return "Circles have constant radius all around.";
  }
}
```

- Instance methods: called on objects (`c.area()`).
- `static` methods: called on the class itself (`Circle.describe()`).

  

### **Inheritance (Extending Classes)**

```JavaScript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    return `${this.name} makes a sound.`;
  }
}

class Dog extends Animal {
  speak() {
    return `${this.name} barks.`;
  }
}

const d = new Dog("Rex");
console.log(d.speak()); // "Rex barks."
```

- `extends` lets a class **inherit** from another.
- Use `super(...)` to call the parent constructor/method.

  

### **Using** `**super()**`

```JavaScript
class Vehicle {
  constructor(type) {
    this.type = type;
  }
}

class Car extends Vehicle {
  constructor(type, model) {
    super(type); // must call parent constructor
    this.model = model;
  }
}
```

- `super()` must be called before using `this` in child class constructors.

  

### **Private Fields (**`**#**`**)**

```JavaScript
class BankAccount {
  \#balance = 0;

  deposit(amount) {
    this.\#balance += amount;
  }

  getBalance() {
    return this.\#balance;
  }
}
```

- `#` makes a field truly private (cannot be accessed outside).

  

### **Getters and Setters**

```JavaScript
class User {
  constructor(name) {
    this._name = name;
  }

  get name() {
    return this._name.toUpperCase();
  }

  set name(value) {
    this._name = value.trim();
  }
}
```

- Use `get` and `set` to control property access like a variable.

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Syntax / Example|Notes|
|Class declaration|`class Name {}`|Defines a class blueprint|
|Constructor|`constructor(...) {}`|Runs when object is created|
|Instance method|`method() {}`|Belongs to each instance|
|Static method|`static method() {}`|Called on the class itself|
|Inheritance|`class Child extends Parent`|Reuse logic from parent class|
|super()|`super(...)`|Calls parent constructor/method|
|Private field|`#privateVar`|Only accessible within the class|
|Getter/Setter|`get name()`, `set name(val)`|Control access to properties|

  

```JavaScript
class Product {
    constructor(name, price) {
        this.name = name;
        this.price = price;
    }
    displayProduct() {
        console.log(`Product: ${this.name}`);
        console.log(`Product: $${this.price.toFixed(2)}`);
    }
    calculateTOtal(salesTax) {
        return this.price + this.price * salesTax;
    }
}

const sales = 0.05;

const product1 = new Product("Shirt", 19.959);
const product2 = new Product("Pants", 25.959);

const total1 = product1.calculateTOtal(sales);
const total2 = product2.calculateTOtal(sales);

product1.displayProduct();
console.log(`Total price (with tax): $${total1.toFixed(2)}`);
console.log(``);
product2.displayProduct();
console.log(`Total price (with tax): $${total2.toFixed(2)}`);
```