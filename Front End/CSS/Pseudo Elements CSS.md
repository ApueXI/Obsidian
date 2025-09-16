---
Created: 2025-06-10T11:30
---
## ==What Are Pseudo-Elements?==

**Pseudo-elements** let you style **specific parts** of an element or insert **generated content** without needing extra HTML elements.

  

### Syntax

```CSS
selector::pseudo-element {
  /* styles */
}
```

> (Some older browsers support :pseudo-element, but :: is the standard.)

  

## Common Pseudo-Elements

|   |   |   |
|---|---|---|
|Pseudo-Element|Description|Example|
|`::before`|Inserts content **before** element content|`p::before`|
|`::after`|Inserts content **after** element content|`h1::after`|
|`::first-line`|Styles **first line** of text|`p::first-line`|
|`::first-letter`|Styles **first letter** of text|`p::first-letter`|
|`::selection`|Styles the **highlighted/selected** text|`::selection`|
|`::placeholder`|Styles **placeholder text** in inputs|`input::placeholder`|
|`::marker`|Styles the **bullet or number** in lists|`li::marker`|
|`::cue`|Styles WebVTT captions (used in media)|`::cue`|

  

  

## Example: `::before` and `::after`

```CSS
h1::before {
  content: "🔥 ";
}

h1::after {
  content: " 🚀";
}
```

> Adds emojis **before** and **after** the `<h1>` text.

  

## `::first-letter` & `::first-line`

```CSS
p::first-letter {
  font-size: 200%;
  color: red;
}

p::first-line {
  font-weight: bold;
}
```

Styles the **first letter** and the **first line** of a paragraph differently.

  

## `::selection`

```CSS
::selection {
  background: yellow;
  color: black;
}
```

Styles **text when selected** by the user (highlighted with mouse).  
  

## `::placeholder`

```CSS
input::placeholder {
  color: gray;
  font-style: italic;
}
```

Styles the **placeholder text** in form inputs.

  

## `::marker` (List bullets/numbers)

```CSS
li::marker {
  color: green;
  content: "✔ ";
}
```

Changes the color or symbol of list bullets or numbers.

  

## `content` Property

Used **only with** `**::before**` **and** `**::after**` to insert content:

```CSS
.element::before {
  content: "Note: ";
}
```

Can also include:

- `""` for empty
- `attr(data-label)` to pull attribute content
- Unicode: `\2713` (✔), `\00A0` (space)

  

## Summary Table

|   |   |
|---|---|
|Pseudo-Element|Use Case|
|`::before` / `::after`|Inject content|
|`::first-line` / `::first-letter`|Typography effects|
|`::selection`|Custom highlight|
|`::placeholder`|Form UX|
|`::marker`|List customization|

  

pseudo-element =keyword added after a selector that's used to style a specific parts of an element

selector:: pseudo-element

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="PseudoElements.css">
    <title>Pseudo Elements</title>
</head>

<body>

    <h1>Hello</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Delectus porro quod inventore commodi est, possimus
        facilis! Soluta earum ipsa culpa inventore voluptate, sint laboriosam, accusantium ducimus delectus, assumenda
        necessitatibus quasi!</p>
    <ul id="fruit">
        <li id="apple">apple</li>
        <li id="orange">orange</li>
        <li id="banana">banana</li>
    </ul>

</body>

</html>
```

```CSS
h1::first-letter {
    font-size: 2em;
    font-style: italic;
}

p::first-line {
    background-color: yellow;
}

p::selection {
    color: green;
    background-color: darkgrey;
}

\#fruit li::before {
    content: "✔️";
}

\#apple::after {
    content: "✖️";
}

\#banana::after {
    content: "✖️";
}
\#fruit li::marker{
    content: "⭐";
}
```