---
Created: 2025-06-09T19:44
---
display property = specifies if/how an element is displayed

block-level = start on a new line, take up the full width available (h1, div, p, form, header, footer)

inline = do not start on a new line, width is limited to what is needed (span, a, img)

  

`display` – How Elements Are Displayed in the Layout

```CSS
display: value;
```

  

## COMMON `display` VALUES

|   |   |
|---|---|
|Value|Description|
|`none`|Hides the element completely (no layout space).|
|`block`|Element takes full width, starts on a new line.|
|`inline`|Element flows with text, cannot set width/height.|
|`inline-block`|Like inline, but allows width/height.|
|`flex`|Turns container into a **flexbox** (1D layout).|
|`inline-flex`|Same as `flex`, but behaves like `inline`.|
|`grid`|Turns container into a **grid** (2D layout).|
|`inline-grid`|Same as `grid`, but inline.|
|`table`|Behaves like an HTML `<table>`.|
|`table-row`|Behaves like a table row.|
|`table-cell`|Behaves like a table cell.|

## BASIC DISPLAY TYPES

|   |   |   |   |
|---|---|---|---|
|Display|Block-like?|Inline-like?|Can Set Width/Height?|
|`block`|✅ Yes|❌ No|✅ Yes|
|`inline`|❌ No|✅ Yes|❌ No|
|`inline-block`|❌ No|✅ Yes|✅ Yes|

  

## FLEX & GRID DISPLAYS

==flex==

```CSS
display: flex;
justify-content: space-between;
align-items: center;
```

==grid==

```CSS
display: grid;
grid-template-columns: repeat(3, 1fr);
```

  

ADVANCED VALUES

|   |   |
|---|---|
|Value|Description|
|`contents`|Makes the element disappear visually but keep its children visible in layout.|
|`run-in`|Rarely used. Acts as block or inline depending on context.|
|`list-item`|Behaves like a list item (e.g., with bullets/numbering).|

  

## `display: none` vs `visibility: hidden`

|   |   |   |
|---|---|---|
|Property|Visible?|Takes up space?|
|`display: none`|❌ No|❌ No|
|`visibility: hidden`|❌ No|✅ Yes|

  

COMBINED EXAMPLES

```CSS
/* Inline box with width */
span {
  display: inline-block;
  width: 100px;
  height: 50px;
}

/* Hide an element */
.hidden {
  display: none;
}

/* Responsive layout */
@media (max-width: 600px) {
  nav {
    display: block;
  }
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Display Property</title>
</head>
<body>
    

    <h1>Display Property</h1>
    <p>The <code>display</code> property in CSS specifies how an element is displayed on the page. It can take various values, each affecting the layout and visibility of the element.</p>

    <h2>Common Values</h2>
    <ul>
        <li><code>block</code>: The element is displayed as a block-level element, taking up the full width available.</li>
        <li><code>inline</code>: The element is displayed as an inline element, only taking up as much width as necessary.</li>
        <li><code>inline-block</code>: The element is displayed as an inline-level block container.</li>
        <li><code>none</code>: The element is not displayed at all (it will not take up any space).</li>
        <li><code>flex</code>: The element becomes a flex container, allowing for flexible layouts.</li>
        <li><code>grid</code>: The element becomes a grid container, enabling grid-based layouts.</li>
    </ul>

    <h2>Example Usage</h2>
    <pre><code>

</body>
</html>
```

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="DispayProperty.css">
    <title>Display Property</title>
</head>

<body>

    <div id="divs">div</div>

    <span id="spans">span</span>

    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Veritatis, possimus natus suscipit perspiciatis omnis
    reiciendis placeat quasi? Sed, rem? Corporis fuga blanditiis consequatur, sit commodi quisquam voluptas consequuntur
    placeat ducimus!

</body>

</html>
```

```CSS
\#divs {
    background-color: blue;
    width: 100px;
    height: 100px;
    display: inline-block;
    visibility: hidden;
}

\#spans {
    background-color: red;
    width: 100px;
    height: 100px;
    display: none;
}
```