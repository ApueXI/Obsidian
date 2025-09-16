---
Created: 2025-06-13T10:50
---
## JavaScript Arithmetic Operators Cheat Sheet

### 📋 List of Operators

|   |   |   |   |   |
|---|---|---|---|---|
|Operator|Symbol|Description|Example|Result|
|Addition|`+`|Adds two values|`5 + 3`|`8`|
|Subtraction|`-`|Subtracts right from left|`10 - 4`|`6`|
|Multiplication|`*`|Multiplies values|`6 * 2`|`12`|
|Division|`/`|Divides left by right|`9 / 3`|`3`|
|Modulus (Remainder)|`%`|Remainder of division|`10 % 3`|`1`|
|Exponentiation|`**`|Raises to power|`2 ** 3`|`8`|
|Increment|`++`|Adds 1 to the value|`let a = 5; a++`|`6`|
|Decrement|`--`|Subtracts 1|`let b = 5; b--`|`4`|

### Examples

```JavaScript
let x = 10;
let y = 4;

console.log(x + y);  // 14
console.log(x - y);  // 6
console.log(x * y);  // 40
console.log(x / y);  // 2.5
console.log(x % y);  // 2
console.log(x ** 2); // 100
```

  

### Increment / Decrement (Prefix vs Postfix)

```JavaScript
let a = 5;

console.log(a++); // 5 (then becomes 6)
console.log(++a); // 7 (increment first, then log)

let b = 5;
console.log(b--); // 5 (then becomes 4)
console.log(--b); // 3 (decrement first, then log)
```

  

### Combined with Assignment

|   |   |   |   |
|---|---|---|---|
|Operation|Syntax|Example|Equivalent|
|Add & Assign|`+=`|`x += 2`|`x = x + 2`|
|Subtract & Assign|`-=`|`x -= 3`|`x = x - 3`|
|Multiply & Assign|`*=`|`x *= 4`|`x = x * 4`|
|Divide & Assign|`/=`|`x /= 2`|`x = x / 2`|
|Modulus & Assign|`%=`|`x %= 3`|`x = x % 3`|

  

```JavaScript
let students = 30;
students = students + 5; // Adding 5 more students
students = students - 2; // Removing 2 students
students = students * 2; // Doubling the number of students
students = students / 2; // Halving the number of students
// students = students % 3; // Finding the remainder when divided by 3
students = students ** 2; // Squaring the number of students
// students = students++; // Incrementing the number of students (not recommended in this context)
// students = students--; // Decrementing the number of students (not recommended in this context)
students += 2;
students -= 2;
students *= 2;
students /= 2;
students++;
students--;

let result = 1 + 2 * 3 + 4 ** 2;
let diffresult = (1 + 2 )* (3 + 4) ** 2;


console.log("Total number of students:", students); // Output the final count
console.log(result)
console.log(diffresult)
```