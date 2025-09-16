---
Created: 2025-06-07T11:29
---
## **Color Values in CSS**

|   |   |   |
|---|---|---|
|Type|Example|Description|
|**Named colors**|`red`, `blue`, `green`, `black`|Predefined standard names|
|**Hexadecimal**|`#FF0000`, `#00FF00`, `#000000`|Red, Green, Blue in hex|
|**RGB**|`rgb(255, 0, 0)`|Red, Green, Blue (0–255)|
|**RGBA**|`rgba(255, 0, 0, 0.5)`|Adds alpha (opacity) 0–1|
|**HSL**|`hsl(0, 100%, 50%)`|Hue (0–360), Saturation, Lightness|
|**HSLA**|`hsla(0, 100%, 50%, 0.5)`|HSL with alpha transparency|
|**Transparent**|`transparent`|Fully see-through color|

  

## **Common Named Colors**

- Basic: `black`, `white`, `gray`, `red`, `blue`, `green`
- Others: `aqua`, `fuchsia`, `navy`, `teal`, `maroon`, `olive`, `lime`, `silver`

> ✅ There are 147 named colors in CSS.

  

## **HEX Color Syntax**

```CSS
color: \#RRGGBB;
color: \#FF0000;   /* red */
color: \#00FF00;   /* green */
color: \#0000FF;   /* blue */
```

- Shorthand: `#F00` → `#FF0000`

  

## **RGB / RGBA**

```CSS
color: rgb(255, 0, 0);       /* red */
background-color: rgba(0, 0, 0, 0.5);  /* semi-transparent black */
```

- Values: `0–255`
- Alpha (opacity): `0` (invisible) to `1` (fully visible)

  

## **HSL / HSLA**

```CSS
color: hsl(240, 100%, 50%);     /* blue */
color: hsla(0, 100%, 50%, 0.5); /* semi-transparent red */
```

- **Hue**: angle on the color wheel (0–360)
- **Saturation**: 0% (gray) to 100% (full color)
- **Lightness**: 0% (black) to 100% (white)

  

## **Opacity vs Alpha**

- Use `opacity` for entire element:

```CSS
div {
  opacity: 0.7;
}
```

- Use `rgba` or `hsla` to set transparency **only for color**:

```CSS
background: rgba(0, 0, 0, 0.5);
```

  

## **CSS Color Properties**

|   |   |
|---|---|
|Property|Description|
|`color`|Text color|
|`background-color`|Background color|
|`border-color`|Border color|
|`outline-color`|Outline color|
|`fill`|For SVG shapes|
|`stroke`|For SVG lines|

  

## Example

```CSS
.card {
  color: white;
  background-color: hsl(200, 80%, 40%);
  border: 2px solid #333;
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Colors</title>
    <link rel="stylesheet" href="Colors.css">
</head>

<body id="bodys">

    <p id="p1">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Consequatur, et assumenda est earum quibusdam
        laborum, sed quaerat hic odio maxime sint modi deserunt temporibus doloribus necessitatibus labore, voluptatem
        tempore facilis!</p>
    <p id="p2">Dolore iusto consequuntur sunt illo corrupti quibusdam libero vero obcaecati vel cumque eveniet, debitis,
        in sed laborum placeat dolores dicta quis. Consequuntur rem harum excepturi neque nobis eius blanditiis id?</p>
    <p id="p3">Architecto alias, quibusdam provident a voluptate libero eaque excepturi inventore animi necessitatibus
        sed suscipit id officia placeat nam ipsam autem dolorem ipsa assumenda ea quisquam. Numquam aperiam perferendis
        aut error.</p>
    <p id="p4">Repudiandae voluptatum quod veritatis eveniet minus quibusdam porro laudantium impedit, facilis ullam
        voluptas neque provident. Delectus totam molestias laborum laudantium ad incidunt, nostrum quas nemo dolorum
        dolore atque illum inventore!</p>
    <p id="p5">Numquam enim ipsum, voluptas hic, temporibus iure blanditiis aspernatur dignissimos accusantium minus,
        illo quam animi delectus tempora velit harum labore voluptates quia soluta assumenda necessitatibus consequatur.
        Distinctio nemo nesciunt facere!</p>

</body>

</html>
```

```CSS
\#bodys{
    background-color: slategray;
}
\#p1{
    color: tomato;
}
\#p2{
    color: rgb(102, 222, 255);
}
\#p3{
    color: \#59ff5f;
}
\#p4{
    color: hsl(0, 38%, 57%);
}
```