---
Created: 2025-06-21T09:47
---
## Use `#` instead of `_` for truly private data

  

### **What Are Getters and Setters?**

- **Getters** let you access properties like a variable.
- **Setters** let you run code when assigning a value.
- Used for **encapsulation**, **validation**, and **computed values**.

  

### **Basic Getter and Setter**

```JavaScript
class Person {
  constructor(name) {
    this._name = name; // Use underscore for internal property
  }

  get name() {
    return this._name.toUpperCase(); // custom logic
  }

  set name(value) {
    this._name = value.trim(); // custom logic
  }
}

const p = new Person(" Alice ");
console.log(p.name); // "ALICE" (getter called)
p.name = "   Bob   "; // setter called
console.log(p.name); // "BOB"
```

- `get` makes a method behave like a property.
- `set` runs when assigning a value.

  

### **Getter Without Setter (Read-Only)**

```JavaScript
class Circle {
  constructor(radius) {
    this.radius = radius;
  }

  get area() {
    return Math.PI * this.radius ** 2;
  }
}

const c = new Circle(10);
console.log(c.area); // Read-only: 314.15...
```

- **Only** `**get**`: no one can set `area` directly.

  

### **Setter Without Getter (Write-Only)**

```JavaScript
class Secret {
  set code(value) {
    this._hidden = `Encrypted(${value})`;
  }
}

const s = new Secret();
s.code = "12345";
console.log(s._hidden); // "Encrypted(12345)"
```

- Useful for hiding internal logic.

  

### **Object Literal Getters/Setters**

```JavaScript
const user = {
  _age: 18,

  get age() {
    return this._age;
  },

  set age(value) {
    if (value >= 0) this._age = value;
  }
};

console.log(user.age); // 18
user.age = 25;
console.log(user.age); // 25
```

- Works the same way outside of classes using object literals.

  

### Can you use `get` and `set` **without** having the actual property?

✅ **Yes**, and that’s **exactly how they’re meant to work**.

You don’t need to manually define a property like `width` — as long as you define a `**get width()**` or `**set width(value)**`, JavaScript **automatically makes** `**width**` **behave like a property**.

  

### How it works:

```JavaScript
class Rectangle {
    set width(value) {
        this._width = value; // store in a backing field
    }

    get width() {
        return this._width; // retrieve from backing field
    }
}

const rect = new Rectangle();
rect.width = 100;        // ✅ setter is called
console.log(rect.width); // ✅ getter is called
```

  

### Use `#private` fields (Real Encapsulation, ES2022+)

```JavaScript
class Rectangle {
    \#width;
    \#height;

    constructor(width, height) {
        this.\#width = width;
        this.\#height = height;
    }

    get width() {
        return this.\#width;
    }

    set width(value) {
        if (value > 0) this.\#width = value;
    }
}
```

**Pros:**

- Truly private — cannot be accessed outside the class
- Modern and secure

**Cons:**

- Slightly more typing
- Requires modern JS engine (all modern browsers support it now)

  

The underscore `_` is often used as a **convention** to indicate "this is a private or internal property," but it’s **not enforced by JavaScript itself**. The `#` syntax, on the other hand, is an official language feature for **true private fields**.

### Differences between `_` and `#`:

|   |   |   |
|---|---|---|
|Feature|Using `_` (underscore)|Using `#` (private field)|
|**Enforcement**|Just a naming convention, no actual privacy.|Language-enforced privacy; cannot be accessed outside the class.|
|**Access from outside**|You _can_ still access or modify it externally (e.g., `obj._secret`).|You **cannot** access it outside class scope (syntax error if you try).|
|**Tools / Linters**|Linters can warn if you use `_`-prefixed members externally, but no guarantee.|JavaScript engine enforces it at runtime and compile time.|
|**Browser support**|Works everywhere, no new syntax needed.|Supported in modern browsers and Node.js (relatively recent feature).|
|**Syntax**|Just normal properties with underscore names.|Special syntax: prefix with `#`.|

  

### Example with underscore:

```JavaScript
class Person {
  constructor(name) {
    this._name = name; // underscore prefix to signal "private"
  }

  getName() {
    return this._name;
  }
}

const p = new Person('Alice');
console.log(p._name); // "Alice" - still accessible from outside!
```

### Example with `#`:

```JavaScript
js
CopyEdit
class Person {
  \#name; // true private field

  constructor(name) {
    this.\#name = name;
  }

  getName() {
    return this.\#name;
  }
}

const p = new Person('Alice');
console.log(p.\#name); // SyntaxError!
```

  

### Summary

- `_` is just a **convention**: developers agree "don’t touch this," but nothing stops you.
- `#` is **actual private**: enforced by JavaScript, more secure encapsulation.

  

Even though you **never directly declared a property called** `**width**`, JavaScript acts like it’s a real property, because you created `get` and `set` methods.

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Syntax Example|Behavior|
|Getter|`get name() { return ... }`|Access like a property|
|Setter|`set name(value) { ... }`|Assign like a property|
|Read-only|Only getter|Can’t modify from outside|
|Write-only|Only setter|Can’t read from outside|
|Internal var|Use `_name` or `#name`|Avoid naming conflict with public access|

```JavaScript
class Rectangle {
    constructor(width, height) {
        this.width = width;
        this.height = height;
    }
    set width(newWidth) {
        if (newWidth > 0) {
            this._width = newWidth;
        } else {
            console.error(`Width must be a positive number`);
        }
    }
    set height(newheight) {
        if (newheight > 0) {
            this._height = newheight;
        } else {
            console.error(`Height must be a positive number`);
        }
    }
    get width() {
        return this._width.toFixed(2);
    }
    get height() {
        return this._height.toFixed(2);
    }
}

const rectangle = new Rectangle(1000000000, 200);

rectangle.width = 5;
rectangle.height = 6;

console.log(rectangle.width);
console.log(rectangle.height);
```

  

```JavaScript
class Person {
    constructor(firstname, lastname, age) {
        this.firstname = firstname;
        this.lastname = lastname;
        this.age = age;
    }
    set firstname(newFN) {
        if (typeof newFN === "string" && newFN.length > 0) {
            this._firstname = newFN;
        } else {
            console.error(`First name must be a non empty string`);
        }
    }
    set lastname(newLN) {
        if (typeof newLN === "string" && newLN.length > 0) {
            this._lastname = newLN;
        } else {
            console.error(`Last name must be a non empty string`);
        }
    }
    set age(newAge) {
        if (typeof newAge === "number" && newAge > 0) {
            this._age = newAge;
        } else {
            console.error(`Age must be a positive number`);
        }
    }
    get firstname() {
        return this._firstname;
    }
    get lastname() {
        return this._lastname;
    }
    get age() {
        return this._age;
    }
    get fullInfo() {
        return `I am ${this._firstname} ${this._lastname} and i am ${this.age} years old`;
    }
}

const person = new Person("Laren", "Acob", 19);

console.log(person.firstname);
console.log(person.lastname);
console.log(person.age);
console.log(person.fullInfo);
```