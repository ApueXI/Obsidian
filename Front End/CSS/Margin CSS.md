---
Created: 2025-06-09T09:22
---
`margin` – OUTSIDE SPACING

margin: top right bottom left;

margin: value; /* all sides _/_  
_margin: vertical horizontal; /_ top/bottom, left/right */

  

Margin Shorthand Values

|   |   |
|---|---|
|Syntax|Meaning|
|`margin: 10px;`|All 4 sides = 10px|
|`margin: 10px 20px;`|Top/bottom = 10px, Left/right = 20px|
|`margin: 10px 20px 30px;`|Top = 10px, Left/right = 20px, Bottom = 30px|
|`margin: 10px 15px 20px 25px;`|Top = 10px, Right = 15px, Bottom = 20px, Left = 25px|

> 🧠 **Order**: Top → Right → Bottom → Left (TRBL = "Trouble" to remember easily)

  

## Individual Margin Properties

|   |   |   |
|---|---|---|
|Property|Example|Description|
|`margin-top`|`margin-top: 10px;`|Top margin only|
|`margin-right`|`margin-right: 20px;`|Right margin only|
|`margin-bottom`|`margin-bottom: 30px;`|Bottom margin only|
|`margin-left`|`margin-left: 40px;`|Left margin only|

  

## Special Values

|   |   |
|---|---|
|Value|Description|
|`auto`|Automatically adjust margin (useful for centering)|
|`0`|No margin|
|Negative values|Pull elements closer (not always recommended)|

  

```CSS
/* Equal margin on all sides */
margin: 20px;

/* Horizontal center */
margin: 0 auto;  /* top/bottom = 0, left/right = auto */

/* Top and bottom only */
margin: 20px 0;

/* Negative margin (pull inward) */
margin: -10px;
```

  

## Collapsing Margins (Important Concept)

When vertical margins of two elements touch, the **larger one wins**, and they collapse into a single margin space.

```CSS
<div style="margin-bottom: 20px;"></div>
<div style="margin-top: 30px;"></div>
<!-- Total space = 30px, NOT 50px -->
```

  

## Responsive Margin (using % or media queries)

```CSS
margin: 5%;              /* 5% of containing block's width */
@media (max-width: 600px) {
  margin: 10px;
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Margin.css">
    <title>Margin</title>
</head>

<body id="body">

    <div class="box" id="box1">Box 1</div>
    
    <div class="box" id="box2">Box 2</div>

</body>

</html>
```

```CSS
\#body{
    margin: 20px;
}
.box{
    border: 5px solid;
    font-size: 5em;
    width: 250px;
    height: 250px;
}
\#box1{
    background-color: red;
    margin-top: 50px;
    margin-left: 50px;
}
\#box2{
    background-color: blue;
    margin: auto;
}
```