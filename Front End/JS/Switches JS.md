---
Created: 2025-06-16T07:17
---
### **Basic Syntax**

```JavaScript
switch (expression) {
  case value1:
    // code if expression === value1
    break;
  case value2:
    // code if expression === value2
    break;
  default:
    // code if no cases match
}
```

  

### **Example**

```JavaScript
let fruit = "apple";

switch (fruit) {
  case "banana":
    console.log("It's a banana!");
    break;
  case "apple":
    console.log("It's an apple!");
    break;
  default:
    console.log("Unknown fruit");
}
```

**Output:** `It's an apple!`

  

### `**break**` **is Important**

- Stops the switch from **falling through** to the next case.
- If omitted, it will execute **all cases below the match**.

  

### **Multiple Cases (Same Result)**

```JavaScript
let day = "Saturday";

switch (day) {
  case "Saturday":
  case "Sunday":
    console.log("Weekend!");
    break;
  default:
    console.log("Weekday");
}
```

  

### **When to Use** `**switch**` **vs** `**if**`

|   |   |
|---|---|
|Use `switch` when:|Use `if` when:|
|Comparing **one value**|Comparing **different things**|
|Many exact matches|Complex conditions (>, <, etc.)|
|Cleaner than multiple `if`|Need logical operators (`&&`, `|

  

```JavaScript
let score = 20;
let grade;
switch (true) {
  case score >= 90:
    grade = "A";
    break;
  case score >= 80:
    grade = "B";
    break;
  case score >= 70:
    grade = "C";
    break;
  case score >= 60:
    grade = "D";
    break;
  default:
    grade = 'F'
    break;
}
console.log(grade)
```