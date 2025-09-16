---
Created: 2025-06-06T15:45
---
## Summary Table

|   |   |
|---|---|
|Tag|Use|
|`<ul>`|Unordered list|
|`<ol>`|Ordered list|
|`<li>`|List item (used in both `<ul>` and `<ol>`)|
|`<dl>`|Description list|
|`<dt>`|Description term|
|`<dd>`|Description detail|

## HTML Lists Cheat Sheet

There are **three main types of lists** in HTML:

|   |   |   |
|---|---|---|
|Type|Tag|Description|
|**Ordered List**|`<ol>`|Numbered list|
|**Unordered List**|`<ul>`|Bulleted list|
|**Description List**|`<dl>`|List of terms and descriptions|

  

## **Ordered List** `**<ol>**`

Items are **numbered** (1, 2, 3…).

```HTML
<ol>
  <li>First item</li>
  <li>Second item</li>
</ol>
```

**Attributes:**

- `type="A"` → A, B, C…
- `type="i"` → i, ii, iii…
- `start="5"` → Starts numbering at 5
- `reversed` → Reverses order (from 3 to 1)

```HTML
<ol type="A" start="3" reversed>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>
```

  

## **Unordered List** `**<ul>**`

Items are marked with **bullets**.

```HTML
<ol type="A" start="3" reversed>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>
```

**Styling with CSS:**

```CSS
ul {
  list-style-type: square; /* circle, disc, none */
}
```

  

## **Description List** `**<dl>**`

Used for **terms and definitions**.

```HTML
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets</dd>
</dl>
```

|   |   |
|---|---|
|Tag|Meaning|
|`<dl>`|Description list container|
|`<dt>`|Term name|
|`<dd>`|Term description|

  

## **Nested Lists**

Lists can be **nested inside each other**:

```HTML
<ul>
  <li>Fruits
    <ul>
      <li>Apple</li>
      <li>Orange</li>
    </ul>
  </li>
  <li>Vegetables</li>
</ul>
```

  

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

    <!-- Unordered List -->
    <h4>Groceries</h4>
    <ul>
        <li>Milk</li>
        <li>Egg</li>
        <li>Breas</li>
        <li>Coffee</li>
    </ul>

    <!-- Ordered List -->
    <h4>To do</h4>
    <ol>
        <li>Sleep</li>
        <li>Eat</li>
        <li>Walk</li>
        <li>Run</li>
    </ol>

    <!-- Description List -->
    <h4>Description</h4>
    <dl>
        <dt>Dragon</dt>
        <dd>Black dragon fatalis</dd>

        <dt>Slime</dt>
        <dd>Lord of Jura</dd>

        <dt>Paladin</dt>
        <dd>Tank</dd>

        <dt>Knight</dt>
        <dd>All Around</dd>

    </dl>

</body>

</html>
```