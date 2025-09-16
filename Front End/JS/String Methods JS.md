---
Created: 2025-06-17T11:40
---
### **Basic Properties & Access**

|   |   |   |
|---|---|---|
|Method/Property|Description|Example|
|`length`|Returns string length|`"hello".length` → `5`|
|`charAt(index)`|Character at index|`"hi".charAt(0)` → `'h'`|
|`at(index)`|(new) char at index (supports -1)|`"hi".at(-1)` → `'i'`|
|`[index]`|Shortcut for charAt|`"hi"[1]` → `'i'`|

  

### **Modifying Strings**

|   |   |   |
|---|---|---|
|Method|Description|Example|
|`toUpperCase()`|All uppercase|`"hi".toUpperCase()` → `'HI'`|
|`toLowerCase()`|All lowercase|`"HI".toLowerCase()` → `'hi'`|
|`trim()`|Remove spaces from both ends|`" hi ".trim()` → `'hi'`|
|`replace(a, b)`|Replace first match|`"hi".replace("h", "y")` → `'yi'`|
|`replaceAll(a, b)`|Replace all matches|`"ha ha".replaceAll("ha", "yo")`|

  

### **Finding Content**

|   |   |   |
|---|---|---|
|Method|Description|Example|
|`includes("txt")`|Checks if it exists|`"hello".includes("ell")` → `true`|
|`startsWith("txt")`|Starts with|`"hi".startsWith("h")` → `true`|
|`endsWith("txt")`|Ends with|`"hi".endsWith("i")` → `true`|
|`indexOf("txt")`|First position of match|`"hello".indexOf("e")` → `1`|
|`lastIndexOf("txt")`|Last match position|`"hello".lastIndexOf("l")` → `3`|

  

### **Cutting Strings**

|   |   |   |
|---|---|---|
|Method|Description|Example|
|`slice(start, end)`|Slice part (end not included)|`"hello".slice(1, 3)` → `'el'`|
|`substring(start, end)`|Like `slice` but no negative|`"hello".substring(1, 3)` → `'el'`|
|`substr(start, length)`|(Deprecated) use `slice`|`"hello".substr(1, 2)` → `'el'`|
|`split("sep")`|Splits string into array|`"a,b,c".split(",")` → `['a','b','c']`|

  

### **Combining Strings**

|   |   |   |
|---|---|---|
|Method|Description|Example|
|`concat()`|Combine strings|`"hi".concat(" there")` → `'hi there'`|
|`+` operator|Join strings|`"hi" + " there"` → `'hi there'`|

  

### **Template Literals**

```JavaScript
let name = "John";
let greeting = `Hello, ${name}!`;  // → "Hello, John!"
```

  

### Bonus: Escape Characters

|   |   |
|---|---|
|Character|Meaning|
|`\'`|Single quote|
|`\"`|Double quote|
|`\\`|Backslash|
|`\n`|New line|
|`\t`|Tab|

  

```JavaScript
let username = "Brocode   ";
let phonenumber = '123-456-7890'
let usernames = username.trim();
phonenumber = phonenumber.replaceAll('-', '')

console.log(username.charAt(1));
console.log(username.indexOf("o"));
console.log(username.lastIndexOf("o"));
console.log(username.length);
console.log(usernames);
console.log(username.toUpperCase());
console.log(username.toLocaleLowerCase());
console.log(username.repeat(3));
console.log(username.startsWith('B'));
console.log(username.startsWith('C'));
console.log(username.endsWith(''));
console.log(username.includes(' '));
console.log(phonenumber)
console.log(phonenumber.padStart(15, '0'))
console.log(phonenumber.padEnd(15, '0'))
```