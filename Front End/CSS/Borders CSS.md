---
Created: 2025-06-07T12:25
---
## BASIC BORDER PROPERTIES

|   |   |   |
|---|---|---|
|Property|Example|Description|
|`border`|`border: 1px solid black;`|Shorthand to set width, style, and color of all four borders.|
|`border-width`|`border-width: 2px;`|Sets the width (thickness) of the border. Can be in px, em, rem, etc.|
|`border-style`|`border-style: solid;`|Sets the line style.|
|`border-color`|`border-color: red;`|Sets the color of the border. Can set individual sides.|

  

## BORDER STYLES

|   |   |
|---|---|
|Value|Description|
|`none`|No border|
|`solid`|Single solid line|
|`dashed`|Dashed line|
|`dotted`|Dotted line|
|`double`|Two solid lines|
|`groove`|Carved effect (depends on color)|
|`ridge`|Opposite of groove|
|`inset`|Looks like embedded in the page|
|`outset`|Looks like it's coming out|
|`hidden`|Same as `none`, but used with tables|

  

## INDIVIDUAL BORDER SIDES

|   |   |   |
|---|---|---|
|Property|Example|Description|
|`border-top`|`border-top: 1px solid blue;`|Top border only|
|`border-right`|`border-right: 1px dashed green;`|Right border only|
|`border-bottom`|`border-bottom: 2px double black;`|Bottom border only|
|`border-left`|`border-left: 5px groove gray;`|Left border only|

Each side also has its own:

- `border-top-width`
- `border-top-style`
- `border-top-color` (and similar for right, bottom, left)

  

## BORDER RADIUS (for rounded corners)

|   |   |   |
|---|---|---|
|Property|Example|Description|
|`border-radius`|`border-radius: 10px;`|Rounds all corners equally|
|`border-radius` (individual corners)|`border-top-left-radius: 5px;`|Round a specific corner|

**Shorthand examples:**

- `border-radius: 10px 20px;` → top-left/bottom-right: 10px, top-right/bottom-left: 20px
- `border-radius: 10px 20px 30px 40px;` → top-left, top-right, bottom-right, bottom-left

  

## OUTLINE (not technically border, but similar)

|   |   |   |
|---|---|---|
|Property|Example|Description|
|`outline`|`outline: 2px solid red;`|Draws a line outside the border without affecting layout|
|`outline-offset`|`outline-offset: 5px;`|Space between the border and the outline|

Other tricks

Transparent Borders:

border: 5px solid transparent;

  

Border with background clipping:

background-clip: padding-box;

  

Centered dashed borders:

border: 3px dashed black;  
border-style: dashed;

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Borders.css">
    
    <title>Borders</title>
</head>

<body>
    <h1 id="h1">Cabigan</h1>

    <p id="p1">Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto, dolores velit voluptates alias quasi
        blanditiis optio magnam quod! Sit repudiandae asperiores voluptatem ipsum deleniti temporibus molestiae non at
        illo est.</p>

</body>

</html>
```

```CSS
\#h1{
    /* border-style: double;
    border-width: 5px;
    border-color: blue; */
    /* can also do this instead. short hand syntax */
    border: 2px double blue;
    border-radius: 25px;
}
\#p1{
    border-bottom: 3px solid red;
    border-top: 5px dashed green;
    border-left: dotted 2px orange;
    border-right: double 10px violet;

    border-radius: 10px;
}
```