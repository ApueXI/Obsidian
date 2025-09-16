---
Created: 2025-06-10T08:08
---
`background-image` – Set an Image as Background

```CSS
background-image: url("image.jpg");
```

  

## Full Example:

```CSS
body {
  background-image: url("bg.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
}
```

  

## All Background Properties (Useful Together)

|   |   |
|---|---|
|Property|Description|
|`background-image`|Sets the image itself|
|`background-repeat`|Repeats the image (`repeat`, `no-repeat`, `repeat-x`, `repeat-y`, `space`, `round`)|
|`background-position`|Where the image is placed (`center`, `top`, `bottom right`, `50% 20%`)|
|`background-size`|Image size (`cover`, `contain`, `auto`, `100px 200px`, `100% 100%`)|
|`background-attachment`|Scroll behavior (`scroll`, `fixed`, `local`)|
|`background-color`|Fallback color if image doesn't load|
|`background-clip`|Area the background applies to (`border-box`, `padding-box`, `content-box`)|
|`background-origin`|Where background positioning starts|
|`background-blend-mode`|How background layers blend (`multiply`, `screen`, etc.)|

  

## `background-size` Values

|   |   |
|---|---|
|Value|Description|
|`cover`|Image fills container; may crop|
|`contain`|Entire image fits inside; no crop|
|`auto`|Original size|
|`100% 100%`|Stretch image to fill exactly (can distort)|

  

## `background-position` Values

|   |   |
|---|---|
|Value|Description|
|`left top`, `right bottom`|Corners|
|`center center`|Centered|
|`50% 20%`|X% from left, Y% from top|
|`10px 30px`|X/Y in pixels|

  

## `background-repeat` Options

|   |   |
|---|---|
|Value|Description|
|`repeat`|Repeats in both directions|
|`no-repeat`|Only shows once|
|`repeat-x`|Repeats horizontally|
|`repeat-y`|Repeats vertically|
|`space`|Repeats with equal spacing|
|`round`|Resizes to fit neatly|

  

## Shorthand: `background`

```CSS
background: url("bg.jpg") no-repeat center/cover fixed #000;
```

> Order: `color image repeat position/size attachment`

  

## Tips

- Use high-res images with `cover` for full-screen effects.
- Combine with gradients using `background-image: linear-gradient(...)` + `url(...)`.
- Always set `background-color` as a fallback.

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="BGIMG.css">
    <title>Background Image</title>
</head>

<body>

    <h1>Hello</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sapiente, voluptatibus atque recusandae laboriosam
        tempore autem totam, praesentium nisi corporis reiciendis quod iure perferendis, vitae quos. Accusamus
        voluptatum officia alias illum!</p>

</body>

</html>
```

```CSS
body{
    background-image: url(images/huashiJW_banner.jpg);
    background-repeat: no-repeat;
    background-position: center;
    background-attachment: fixed;
    background-size: cover;
}
```