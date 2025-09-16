---
Created: 2025-06-07T12:25
---
`box-shadow` (for element shadows)

box-shadow: offset-x offset-y blur-radius spread-radius color inset;

box-shadow: 4px 4px 10px 2px rgba(0, 0, 0, 0.25);

  

|   |   |
|---|---|
|Part|Description|
|`offset-x`|Horizontal position of the shadow (positive → right, negative → left)|
|`offset-y`|Vertical position (positive → down, negative → up)|
|`blur-radius`|Optional. How soft or blurry the shadow is (higher = blurrier)|
|`spread-radius`|Optional. How much bigger or smaller the shadow is than the element|
|`color`|Shadow color (can use named colors, hex, rgba, hsl, etc.)|
|`inset`|Optional. Puts the shadow _inside_ the box instead of outside|

  

```CSS
/* Basic shadow */
box-shadow: 2px 2px 5px gray;

/* Soft shadow */
box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);

/* Inset shadow */
box-shadow: inset 0 2px 6px rgba(0, 0, 0, 0.3);

/* Spread shadow */
box-shadow: 0 0 10px 5px rgba(0, 0, 0, 0.15);

/* Multiple shadows */
box-shadow: 1px 1px 3px red, -1px -1px 3px blue;
```

  

`text-shadow` (for text)

text-shadow: offset-x offset-y blur-radius color;

text-shadow: 1px 1px 3px black;

  

|   |   |
|---|---|
|Part|Description|
|`offset-x`|Horizontal shadow offset|
|`offset-y`|Vertical shadow offset|
|`blur-radius`|How blurry the shadow appears|
|`color`|Shadow color|

  

```CSS
/* Basic shadow */
text-shadow: 2px 2px gray;

/* Glowing text */
text-shadow: 0 0 10px cyan;

/* Multiple shadows for layered effect */
text-shadow: 1px 1px 0 black, 2px 2px 0 gray;
```

  

Bonus:

box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);

  

Neumorphism (inset & outset together):

box-shadow:  
8px 8px 15px \#babecc,  
-8px -8px 15px \#ffffff;

  

Glassmorphism (blurred background + soft shadow):

box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);  
backdrop-filter: blur(4px);

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Shadows.css">
    <title>Shadows</title>
</head>
<body>
    
    <h1 class="h1">Cabigan</h1>

    <div id="divs">
        
    </div>

</body>
</html>
```

can add another shadow by adding a comma

```CSS
.h1{
    text-shadow: 3px 3px 5px red, -3px -3px 5px blue;
}
\#divs{
    width: 100px;
    height: 100px;
    background-color: grey;
    box-shadow: 4px 4px 4px;
}
```