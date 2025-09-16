---
Created: 2025-06-21T08:32
---
### What is `super`?

- `super` is used **inside a subclass** (a class that extends another).
- It refers to the **parent class** (superclass).
- Used to:
    - Call the **parent's constructor**.
    - Call **parent methods**.

  

### **Call Parent Constructor**

```JavaScript
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Calls Animal's constructor
    this.breed = breed;
  }
}
```

- `**super(name)**` must be the first line inside the subclass `constructor`.
- You can’t use `this` before calling `super()`.

  

### **Call Parent Method**

```JavaScript
class Animal {
  speak() {
    return `${this.name} makes a sound.`;
  }
}

class Dog extends Animal {
  speak() {
    return super.speak() + ` And barks!`;
  }
}

const rex = new Dog("Rex");
console.log(rex.speak()); // "Rex makes a sound. And barks!"
```

- `super.speak()` calls the method from the parent class (`Animal`).

  

### **Works with Static Methods Too**

```JavaScript
class Parent {
  static greet() {
    return "Hello from parent!";
  }
}

class Child extends Parent {
  static greet() {
    return super.greet() + " And child!";
  }
}

console.log(Child.greet()); // "Hello from parent! And child!"
```

- `super` also works inside **static methods** to call parent static methods.

  

### **Using** `**super**` **Without a** `**constructor**`

```JavaScript
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Cat extends Animal {
  // No constructor needed if you're not adding new properties
}

const c = new Cat("Whiskers");
console.log(c.name); // "Whiskers"
```

- If you don't define a `constructor`, JavaScript automatically adds one that calls `super(...args)`.

  

### Summary Table

|   |   |   |
|---|---|---|
|Use Case|Syntax Example|Notes|
|Call parent constructor|`super(arg1, arg2)`|Must be first line in child `constructor`|
|Call parent method|`super.methodName()`|Calls method from parent class|
|Static method access|`super.method()`|Works in `static` methods too|
|No child constructor needed|Just extend|JS handles `super(...)` automatically|

  

### Using Parenthesis

You can use parenthesis to use keyword arguments

```JavaScript
class Animal {
    constructor({name, age}) {
        this.name = name;
        this.age = age;
    }
}
class Rabbit extends Animal {
    constructor(name, age, runSpeed) {
        super({name, age});
        this.runSpeed = runSpeed;
    }
}
class Hawk extends Animal {
    constructor(name, age, flySpeed) {
        super(name, age);
        this.runSpeed = flySpeed;
    }
}
class Fish extends Animal {
    constructor(name, age, swimSpeed) {
        super(name, age);
        this.runSpeed = swimSpeed;
    }
}

const rabbit = new Rabbit({name:'Rabbit', age:15, runSpeed:60});

console.log(rabbit.name);
console.log(rabbit.age);
console.log(rabbit.runSpeed);
```

  

```JavaScript
class Animal {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    move(speed) {
        console.log(`The ${this.name} moves at a speed of ${speed}`);
    }
}
class Rabbit extends Animal {
    constructor(name, age, runSpeed) {
        super(name, age);
        this.runSpeed = runSpeed;
    }
    run() {
        console.log(`This ${this.name} can run`);
        super.move(this.runSpeed);
    }
}
class Hawk extends Animal {
    constructor(name, age, flySpeed) {
        super(name, age);
        this.flySpeed = flySpeed;
    }
    fly() {
        console.log(`This ${this.name} can swim`);
        super.move(this.flySpeed);
    }
}
class Fish extends Animal {
    constructor(name, age, swimSpeed) {
        super(name, age);
        this.swimSpeed = swimSpeed;
    }
    swim() {
        console.log(`This ${this.name} can fly`);
        super.move(this.swimSpeed);
    }
}

const rabbit = new Rabbit("Rabbit", 15, 60);
const hawk = new Hawk("Hawk", 20, 150);
const fish = new Fish("Fish", 6, 30);

console.log(rabbit.name);
console.log(rabbit.age);
console.log(rabbit.runSpeed);

rabbit.run();
console.log(``);
hawk.fly();
console.log(``);
fish.swim();
console.log(``);
```