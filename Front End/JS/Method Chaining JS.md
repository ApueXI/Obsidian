---
Created: 2025-06-17T18:12
---
### **String Chaining Example**

```JavaScript
let result = "  Hello World  "
  .trim()
  .toUpperCase()
  .slice(0, 5);

console.log(result); // "HELLO"
```

**Explanation:**

- `trim()` → removes whitespace → `"Hello World"`
- `toUpperCase()` → `"HELLO WORLD"`
- `slice(0, 5)` → `"HELLO"`

  

### **Array Chaining Example**

```JavaScript
let numbers = [1, 2, 3, 4, 5];

let doubledEvens = numbers
  .filter(n => n % 2 === 0)
  .map(n => n * 2);

console.log(doubledEvens); // [4, 8]
```

**Steps:**

- `filter()` → keep even numbers → `[2, 4]`
- `map()` → double each → `[4, 8]`

  

### **Custom Object Chaining (with** `**this**`**)**

```JavaScript
let person = {
  name: "",
  setName(n) {
    this.name = n;
    return this;
  },
  greet() {
    console.log("Hi, " + this.name);
    return this;
  }
};

person.setName("Alex").greet(); // Hi, Alex
```

  

### Tips for Chaining

✅ Only works when:

- Each method returns the object (or a value you can keep calling methods on)

🚫 Doesn’t work if:

- One method returns `undefined`, `null`, or a primitive that breaks the chain

  

```JavaScript
// No Method Chaining

let username = window.prompt("Enter your username: ");
let usernames = window.prompt("Enter your username: ");

username = username.trim();
let letter = username.charAt(0);
letter = letter.toUpperCase();
let extraChar = username.slice(1);
extraChar = extraChar.toLowerCase();
username = letter + extraChar;

console.log(username);

// Method Chaining

usernames =
  username.trim().charAt(0).toUpperCase() +
  username.trim().slice(1).toLocaleLowerCase();

console.log(usernames);
```