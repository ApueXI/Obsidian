---
Created: 2025-06-17T16:43
---
### `**slice(start, end)**`

- Returns part of the string.
- `start` is **included**, `end` is **excluded**.
- Supports **negative indexes**.

```JavaScript
let str = "JavaScript";

console.log(str.slice(0, 4));   // "Java"
console.log(str.slice(4));      // "Script"
console.log(str.slice(-6));     // "Script"
console.log(str.slice(-6, -3)); // "Scr"
```

  

### `**substring(start, end)**`

- Similar to `slice()`
- **Does not support negative indexes**
- If `start > end`, it **swaps** them

```JavaScript
let str = "JavaScript";

console.log(str.substring(0, 4));  // "Java"
console.log(str.substring(4, 0));  // "Java" (swaps)
```

  

### `**substr(start, length)**` ⚠️ _(Deprecated)_

- `start`: where to start
- `length`: how many characters to extract
- Still works, but use `slice()` instead

```JavaScript
let str = "JavaScript";

console.log(str.substr(0, 4));  // "Java"
console.log(str.substr(4, 3));  // "Scr"
```

  

### When to Use

|   |   |
|---|---|
|Task|Best Method|
|Use negative indexes|`slice()`|
|Avoid confusion with swapping|`slice()`|
|Old browser support (legacy)|`substring()`|

  

```JavaScript
const fullname = `Bro Code`;

let firstname = fullname.slice(0, fullname.indexOf(` `));
let lastname = fullname.slice(fullname.indexOf(` `) + 1);

console.log(firstname);
console.log(lastname);
```

```JavaScript
const fullname = `Bro Code`;

const email = `brocode@gmail.com`;

let username = email.slice(0, email.indexOf(`@`));
let extension = email.slice(email.indexOf(`@`));

console.log(username);
console.log(extension);
```