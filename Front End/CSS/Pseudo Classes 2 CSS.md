---
Created: 2025-06-10T09:11
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
    
    <ul>
        <li>This is number #1</li>
        <li>This is number #2</li>
        <li>This is number #3</li>
        <li>This is number #4</li>
        <li>This is number #5</li>
        <li>This is number #6</li>
        <li>This is number #7</li>
        <li>This is number #8</li>
        <li>This is number #9</li>
    </ul>

</body>
</html>
```

```CSS
li:hover{
    background-color: yellow;
}
li:not(:hover){
    background-color: grey
}
```