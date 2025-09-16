---
Created: 2025-06-15T09:45
---
### **Basic Random Decimal**

```JavaScript
Math.random();
```

- Returns a **decimal number** between `0` (inclusive) and `1` (exclusive)
- Example: `0.294739...`

  

### **Random Integer (0 to n)**

```JavaScript
Math.floor(Math.random() * (n + 1));
```

- Example: random number from `0` to `10`:

```JavaScript
let rand = Math.floor(Math.random() * 11);
```

  

### **Random Integer Between Two Numbers (min to max)**

```JavaScript
Math.floor(Math.random() * (max - min + 1)) + min;
```

- Example: random number from `5` to `15`:

```JavaScript
let rand = Math.floor(Math.random() * (15 - 5 + 1)) + 5;
```

  

### **Random Decimal Between Two Numbers**

```JavaScript
Math.random() * (max - min) + min;
```

- Example: random **float** between `1.5` and `3.5`:

```JavaScript
let randFloat = Math.random() * (3.5 - 1.5) + 1.5;
```

  

### **Random from an Array**

```JavaScript
let colors = ["red", "blue", "green"];
let randomColor = colors[Math.floor(Math.random() * colors.length)];
```

  

### Tips

- Use `Math.floor()` to get whole numbers.
- Use `Math.round()` if you want normal rounding.
- Always add `+1` if your range is **inclusive** of the max.

  

  

```JavaScript
const button = document.getElementById('button');
const label1 = document.getElementById('label1');
const label2 = document.getElementById('label2');
const label3 = document.getElementById('label3');
const min = 1;
const max = 6;
let randomnum1;
let randomnum2;
let randomnum3;

button.onclick = function(){
    randomnum1 = Math.floor(Math.random() * max) + min;
    randomnum2 = Math.floor(Math.random() * max) + min;
    randomnum3 = Math.floor(Math.random() * max) + min;
    label1.textContent = randomnum1
    label3.textContent = randomnum2
    label2.textContent = randomnum3
}
```

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>M<ath Objects</title>
    <style>
        body {
            font-family: Verdana, Geneva, Tahoma, sans-serif;
            text-align: center;
        }
        \#button{
            font-size: 3em;
            padding: 5px 25px;
            border-radius: 10px;
        }
        .labels{
            font-size: 3em;
        }
    </style>
</head>

<body>

    <button id="button">roll</button><br>
    <label for="button" id="label1" class="labels"></label><br>
    <label for="button" id="label2" class="labels"></label><br>
    <label for="button" id="label3" class="labels"></label><br>

    <script src="../RandomNumGenrator.js"></script>
</body>

</html>
```