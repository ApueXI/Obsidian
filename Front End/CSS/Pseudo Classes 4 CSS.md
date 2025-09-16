---
Created: 2025-06-10T09:21
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
    
    <div id="greeting">Hover Here
        <p>Hello</p>
    </div>
</body>
</html>
```

```CSS
\#greeting p{
    background-color: blue;
    padding: 10px;
    display: none;
}
\#greeting:hover p {
    display: block;
    color: white;
}
```