---
Created: 2025-06-12T17:48
---
## CSS Transform Cheat Sheet

The `transform` property lets you visually manipulate elements using functions like rotate, scale, translate, etc.

  

### Syntax

```CSS
selector {
  transform: transform-function;
}
```

You can combine multiple functions:

```CSS
transform: rotate(45deg) scale(1.2) translateX(20px);
```

  

### Common Transform Functions

|   |   |   |
|---|---|---|
|Function|Description|Example|
|`translateX(px)`|Move horizontally|`translateX(100px)`|
|`translateY(px)`|Move vertically|`translateY(-50px)`|
|`translate(px, px)`|Move both axes|`translate(30px, 60px)`|
|`scale(n)`|Scale both axes|`scale(1.5)`|
|`scaleX(n)`|Scale width|`scaleX(2)`|
|`scaleY(n)`|Scale height|`scaleY(0.5)`|
|`rotate(deg)`|Rotate clockwise|`rotate(45deg)`|
|`skewX(deg)`|Skew horizontally|`skewX(15deg)`|
|`skewY(deg)`|Skew vertically|`skewY(-10deg)`|
|`skew(x, y)`|Skew both directions|`skew(20deg, 10deg)`|
|`matrix(a, b, c, d, e, f)`|Combined 2D transform (advanced)|N/A|

  

### 3D Transform Functions

|   |   |
|---|---|
|Function|Description|
|`rotateX(deg)`|Rotate on X-axis|
|`rotateY(deg)`|Rotate on Y-axis|
|`rotateZ(deg)`|Rotate on Z-axis (same as 2D rotate)|
|`translateZ(px)`|Move in 3D (needs perspective)|
|`scaleZ(n)`|Scale in depth|
|`perspective(px)`|Define a 3D space|

  

### Example

```CSS
.box {
  transform: rotate(45deg) scale(1.2);
  transition: transform 0.3s ease;
}
.box:hover {
  transform: rotate(0deg) scale(1);
}
```

  

### Tips

- Combine with `transition` for smooth effects.
- `transform` doesn't affect layout flow — it's purely visual.
- Use `transform-origin` to set the pivot point (default is center).

```CSS
transform-origin: top left;
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Transformation.css">
    <title>Transformation</title>
</head>
<body>
    
    <div class="box" id="box1">Hi</div>
    <div class="box" id="box2">Hi</div>
    <div class="box" id="box3">Hi</div>

</body>
</html>
```

```CSS
body {
    margin: 0px;
}

.box {
    width: 250px;
    height: 250px;
    border: 5px solid;
    font-size: 13em;
    text-align: center;

    transform: translateX(100px) rotateZ(45deg) scale(0.5);
}

\#box1 {
    background-color: lightgreen;

}
\#box2 {
    background-color: hsl(0, 100%, 64%);

}
\#box3 {
    background-color: lightblue;

}
```