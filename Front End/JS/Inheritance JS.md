---
Created: 2025-06-20T20:41
---
### **What Is Inheritance?**

**Inheritance** lets one class (child/subclass) reuse code from another class (parent/superclass).

  

### **Basic Class Inheritance with** `**extends**`

```JavaScript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    return `${this.name} makes a noise.`;
  }
}

class Dog extends Animal {
  bark() {
    return `${this.name} barks!`;
  }
}

const d = new Dog("Rex");
console.log(d.speak()); // "Rex makes a noise."
console.log(d.bark());  // "Rex barks!"
```

- `Dog` inherits `speak()` from `Animal`.
- Can add extra methods like `bark()`.

  

### **Using** `**super()**` **in Subclass Constructor**

```JavaScript
class Bird extends Animal {
  constructor(name, color) {
    super(name); // Calls parent constructor
    this.color = color;
  }

  info() {
    return `${this.name} is a ${this.color} bird.`;
  }
}
```

- `super(...)` **must be called** before using `this` in a subclass constructor.
- It passes arguments to the parent class.

  

### **Overriding Methods**

```JavaScript
class Cat extends Animal {
  speak() {
    return `${this.name} meows.`;
  }
}

const kitty = new Cat("Mittens");
console.log(kitty.speak()); // "Mittens meows."
```

- Child classes can **override** methods from the parent class.

  

### **Calling Parent Method with** `**super.method()**`

```JavaScript
class Lion extends Animal {
  speak() {
    return super.speak() + " And roars!";
  }
}

const simba = new Lion("Simba");
console.log(simba.speak()); // "Simba makes a noise. And roars!"
```

- Use `super.method()` to call a **method from the parent class**.

  

### **Inheritance with Static Methods**

```JavaScript
class Parent {
  static greet() {
    return "Hello from Parent";
  }
}

class Child extends Parent {}

console.log(Child.greet()); // "Hello from Parent"
```

- **Static methods** are also inherited!

  

### Summary Table

|   |   |   |
|---|---|---|
|Concept|Keyword / Action|Example|
|Inherit a class|`extends`|`class Dog extends Animal`|
|Call parent constructor|`super(...)`|`super(name)` inside `constructor`|
|Call parent method|`super.method()`|`super.speak()`|
|Override method|Define it again in child|`speak()` in `Cat`|
|Inherit static methods|Automatically inherited|`Child.greet()`|

  

```JavaScript
class Animal {
    isAlive = true;
    eat() {
        console.log(`This ${this.name} is eating`);
    }
    sleep() {
        console.log(`This ${this.name} is sleeping`);
    }
}

class Rabbit extends Animal {
    name = "rabbit";
    run() {
        console.log(`This ${this.name} is runnig`);
    }
}
class Fish extends Animal {
    name = "Fish";
    swim() {
        console.log(`This ${this.name} is swimming`);
    }
}
class Hawk extends Animal {
    name = "Hawk";
    fly() {
        console.log(`This ${this.name} is flying`);
    }
}
const rabbit = new Rabbit();
const fish = new Fish();
const hawk = new Hawk();

rabbit.eat();
rabbit.run();
rabbit.sleep();
console.log(``);
fish.eat();
fish.swim();
fish.sleep();
console.log(``);
hawk.eat();
hawk.fly();
hawk.sleep();
console.log(``);
```