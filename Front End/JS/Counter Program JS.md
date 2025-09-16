---
Created: 2025-06-15T07:53
---
```JavaScript
const decrease = document.getElementById('decrease');
const reset = document.getElementById('reset');
const increase = document.getElementById('increase');
const countlabel = document.getElementById('countlabel');
let count = 0;

increase.onclick = function(){
    count++;
    countlabel.textContent = count;
}
reset.onclick = function(){
    count = 0;
    countlabel.textContent = count;
}
decrease.onclick = function(){
    count--;
    countlabel.textContent = count;
}
```

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Counter Program</title>
    <style>
        \#countlabel {
            display: block;
            text-align: center;
            font-size: 10em;
            font-family: sans-serif;
        }

        \#container {
            text-align: center;
        }
        .buttons{
            padding: 10px 20px;
            font-size: 1.5em;
            color: white;
            background-color: black;
            border-radius: 10px;
            cursor: pointer;
            transition: background-color 0.25s;
        }
        .buttons:hover{
            background-color: green;
        }
    </style>
</head>

<body>

    <label for="" id="countlabel">0</label>

    <div id="container">
        <button id="decrease" class="buttons">decrease</button>
        <button id="reset" class="buttons">Reset</button>
        <button id="increase" class="buttons">Increase</button>
    </div>

    <script src="../CounterProgram.js"></script>
</body>

</html>
```