---
Created: 2025-06-20T20:11
---
### **What is** `**static**` **in JS?**

- The `static` keyword defines a **method or property on the class itself**, **not on instances**.
- Think of it as a **"class-level"** method or property.

  

### **Basic Static Method**

```JavaScript
class MathHelper {
  static add(a, b) {
    return a + b;
  }
}

console.log(MathHelper.add(5, 3)); // ✅ 8
```

- You can call `MathHelper.add(...)` directly.
- ❌ You **can’t** call it from an instance:

```JavaScript
const helper = new MathHelper();
helper.add(1, 2); // ❌ TypeError
```

  

### **Static Property**

```JavaScript
class Counter {
  static count = 0;

  static increment() {
    return ++Counter.count;
  }
}

console.log(Counter.increment()); // 1
console.log(Counter.count);       // 1
```

- Static properties are accessed via the class, **not via an object**.

  

### **Static + Instance Side-by-Side**

```JavaScript
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hi, I'm ${this.name}`;
  }

  static description() {
    return "This is the User class.";
  }
}

const u = new User("Alice");
console.log(u.greet());              // ✅ Instance method
console.log(User.description());     // ✅ Static method
```

  

### **Use Case: Utility/Helper Functions**

```JavaScript
class DateUtils {
  static today() {
    return new Date().toLocaleDateString();
  }
}

console.log(DateUtils.today()); // e.g., "6/20/2025"
```

- Great for **methods that don’t depend on instance data**.

  

### **Static with Inheritance**

```JavaScript
class Animal {
  static info() {
    return "Animals are living creatures.";
  }
}

class Dog extends Animal {}

console.log(Dog.info()); // ✅ Inherited static method
```

- Static methods/properties are **inherited by subclasses**.

  

### Summary Table

|   |   |   |   |
|---|---|---|---|
|Feature|Syntax|Called On|Purpose|
|Static method|`static method() {}`|`Class.method()`|Shared logic, no instance needed|
|Static property|`static property = value`|`Class.property`|Class-wide values|
|Access from instance|❌ Not allowed||Only accessible via class|
|Inheritance|✅ Inherited by subclasses||Reusable in class hierarchies|

  

```JavaScript
class MathUtil {
    static PI = 3.14159;

    static getDiameter(radius) {
        return radius * 2;
    }
    static getCircumference(raduis) {
        return 2 * this.PI * raduis;
    }
    static getArea(radius) {
        return this.PI * radius * radius;
    }
}

console.log(MathUtil.PI);
console.log(MathUtil.getDiameter(10));
console.log(MathUtil.getCircumference(10));
console.log(MathUtil.getArea(10));
```

  

```JavaScript
class User {
    static usersCount = 0;

    constructor(username) {
        this.username = username;
        User.usersCount++;
    }
    static getUserCount() {
        console.log(`There are ${User.usersCount} users online`);
    }
    sayHello() {
        console.log(`Hello, my username is ${this.username}`);
    }
}

const user1 = new User("Acob");
const user2 = new User("Andy");
const user3 = new User("Goco");
const user4 = new User("Zam");

console.log(User.usersCount);
user1.sayHello();
User.getUserCount();
```