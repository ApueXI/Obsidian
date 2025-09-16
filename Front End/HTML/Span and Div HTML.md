---
Created: 2025-06-06T12:06
---
## HTML `<span>` and `<div>` Cheat Sheet

Both `<div>` and `<span>` are **generic container elements** used to group or wrap content for styling, layout, or scripting — but they differ in **display behavior**.

  

## **What’s the Difference?**

|   |   |   |
|---|---|---|
|Element|Type|Purpose|
|`<div>`|Block-level|Groups larger sections (layouts, containers)|
|`<span>`|Inline-level|Wraps small parts of text or inline elements|

  

## `**<div>**` **– Block-Level Container**

- Takes up the full width of its parent
- Starts on a **new line**
- Often used for layout and structure

```HTML
<div style="background: lightblue; padding: 10px;">
  This is a div block
</div>
```

  

## `<span>` – Inline Container

- Does **not break** the line
- Wraps **inline text** or elements
- Great for styling a **portion** of text

```HTML
<p>This is a <span style="color: red;">red word</span> in a sentence.</p>
```

  

## **Use Cases**

|   |   |
|---|---|
|Use Case|Use|
|Page sections, cards, columns|`<div>`|
|Coloring or styling part of text|`<span>`|
|JavaScript DOM manipulation targets|Both|

  

## **Styling With CSS**

### For `<div>`:

```CSS
div.box {
  border: 1px solid black;
  padding: 20px;
  margin: 10px;
}
```

### For `<span>`:

```CSS
span.highlight {
  color: yellow;
  background: black;
}
```

  

## **Nested Example**

```HTML
<div class="card">
  <h2>News Title</h2>
  <p>This was written by <span class="author">Jane Doe</span>.</p>
</div>
```

  

## Summary Table

|   |   |   |
|---|---|---|
|Feature|`<div>`|`<span>`|
|Display type|Block-level|Inline-level|
|Line break|Yes|No|
|Layout use|Sections, containers|Inline text styling|
|CSS usage|Width, height, padding, margins|Text styles (color, font, etc.)|
|Scripting use|Yes|Yes|

  

## Quick Tips

- Use `<div>` for **structure**, **layout**, and **grouping blocks** of content.
- Use `<span>` for **styling specific parts** of text **without affecting layout**.
- Always give them **class** or **id** for styling or JavaScript access.

  

span is for inline

div is for block

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <h1>
        <span>
            this is the span title
        </span>
    </h1>
    <h1>
        <div>
            this is the div title
        </div>
    </h1>
</body>

</html>
```