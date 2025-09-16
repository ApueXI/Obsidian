---
Created: 2025-06-10T09:18
---
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="PseudoClasses.css">
    <title>Pseudo Classes</title>
</head>
<body>
    
    <lu>
        <li>This is the number #1</li>
        <li>This is the number #2</li>
        <li>This is the number #3</li>
        <li>This is the number #4</li>
        <li>This is the number #5</li>
        <li>This is the number #6</li>
        <li>This is the number #7</li>
        <li>This is the number #8</li>
        <li>This is the number #9</li>
    </lu>

</body>
</html>
```

```CSS
/* li:nth-child(odd){
    background-color: yellow;
}
li:nth-child(even){
    background-color: yellow;
} */
/* li:nth-child(1){
    background-color: yellow;
} */
/* li:nth-child(3n){
    background-color: yellow;
} */
li:nth-child(2n+1){
    background-color: yellow;
}
```