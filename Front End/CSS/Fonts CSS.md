---
Created: 2025-06-07T11:47
---
## **Font Properties in CSS**

|   |   |
|---|---|
|Property|Description|
|`font-family`|Specifies the font|
|`font-size`|Sets the size of the text|
|`font-weight`|Defines the thickness/boldness|
|`font-style`|Sets normal, italic, or oblique|
|`font-variant`|Small-caps display|
|`line-height`|Space between lines|
|`letter-spacing`|Space between letters|
|`word-spacing`|Space between words|
|`text-transform`|Capitalization (uppercase, etc.)|
|`font`|Shorthand for multiple font properties|

  

## `**font-family**`

```CSS
font-family: "Roboto", Arial, sans-serif;
```

- Lists fallback fonts.
- Use quotes for fonts with spaces.
- Include a **generic family** last (`sans-serif`, `serif`, `monospace`, etc.).

  

### Common Generic Font Families:

|   |   |
|---|---|
|Value|Description|
|`serif`|With strokes (e.g. Times New Roman)|
|`sans-serif`|Without strokes (e.g. Arial)|
|`monospace`|Fixed-width (e.g. Courier New)|
|`cursive`|Handwritten (e.g. Comic Sans MS)|
|`fantasy`|Decorative fonts|

  

## `**font-size**`

```CSS
font-size: 16px;
font-size: 1.2em;
font-size: 120%;
font-size: large;
```

- Units: `px`, `em`, `rem`, `%`
- Relative: `em`, `%`, `larger`, `smaller`
- Absolute: `xx-small` to `xx-large`

  

## `**font-weight**`

```CSS
font-weight: normal;
font-weight: bold;
font-weight: 100; /* thin */
font-weight: 900; /* extra bold */
```

- Numeric scale: `100` (thin) to `900` (extra bold)

  

## `**font-style**`

```CSS
font-style: normal;
font-style: italic;
font-style: oblique;
```

  

## `**font-variant**`

```CSS
font-variant: normal;
font-variant: small-caps;
```

  

## `**line-height**`

```CSS
line-height: 1.5;     /* relative */
line-height: 24px;    /* absolute */
```

  

## `**letter-spacing**` **&** `**word-spacing**`

```CSS
letter-spacing: 1px;
word-spacing: 4px;
```

  

## `**text-transform**`

```CSS
text-transform: uppercase;
text-transform: lowercase;
text-transform: capitalize;
```

  

## **Shorthand:** `**font**`

```CSS
font: italic bold 16px/1.5 "Open Sans", sans-serif;
```

  

## Example:

```CSS
body {
  font-family: "Open Sans", sans-serif;
  font-size: 16px;
  line-height: 1.6;
  font-weight: 400;
  letter-spacing: 0.5px;
}
```

  

## Bonus: Using Google Fonts

```HTML
<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
<style>
body {
  font-family: "Roboto", sans-serif;
}
</style>
```

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fonts</title>
    <link rel="stylesheet" href="Fonts.css">
</head>

<body>

    <h1 id="hh1">Name 1</h1>
    <p id="pp1">Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorem magni non, distinctio earum labore saepe maxime
        odit, autem a, accusamus iusto? Cupiditate eos fuga repudiandae distinctio porro amet quidem. Nihil!</p>
        
</body>

</html>
```

You have to download some fonts

```CSS
@font-face {
    src: url(fonts/example.ttf);
    font-family: example;
}
\#hh1{
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}
\#pp1{
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    font-size: 1em;
    font-weight: bold;
    font-style: italic;
}
```