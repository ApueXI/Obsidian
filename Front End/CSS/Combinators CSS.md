---
Created: 2025-06-10T08:09
---
## ==What Are CSS Combinators?==

CSS **combinators** define the relationship between selectors. They let you **target elements based on their position or relation to others**.

  

## **Descendant Combinator (** **- space)**

Matches all elements that are **inside** another element (any depth).

```CSS
div p {
  color: blue;
}
```

All `<p>` elements **inside** a `<div>`, even nested deeply.

  

## **Child Combinator (**`**>**`**)**

Matches elements that are **direct children**.

```CSS
ul > li {
  list-style-type: square;
}
```

Targets only `<li>` elements that are **directly inside** a `<ul>`, not nested `<li>`.

  

## **Adjacent Sibling Combinator (**`**+**`**)**

Matches an element that is the **next sibling**.

```CSS
h1 + p {
  margin-top: 0;
}
```

Targets the **first** `**<p>**` **that comes right after** an `<h1>`.

  

## **General Sibling Combinator (**`**~**`**)**

Matches **all siblings** after the first element.

```CSS
h1 ~ p {
  color: red;
}
```

Targets **every** `**<p>**` that comes after an `<h1>`, **on the same level**.

  

## Summary Table

|   |   |   |
|---|---|---|
|Combinator|Example|Description|
|(space)|`A B`|B is inside A (any depth)|
|`>`|`A > B`|B is a **direct child** of A|
|`+`|`A + B`|B is the **immediate next sibling** of A|
|`~`|`A ~ B`|B is a **following sibling** of A (any, not just the next)|

  

## Bonus Tip: Combine with Classes/IDs

```CSS
\#menu > li.active + li {
  color: red;
}
```

Selects the `<li>` after the **active** one that is a direct child of `#menu`.  

combinators  
explains the relationship  
between listed selectors  
= descendant

> = child

~ = general sibling

+ = adjacent sibling

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Combinators.css">
    <title>Combinators</title>
</head>

<body>

    <div id="container">
        <p>This is number #1</p>
        <p>This is number #2</p>
        <div>
            <p>
                This is number #3
            </p>
        </div>
    </div>

    <p>This is number #4</p>
    <p>This is number #5</p>

</body>

</html>
```

```CSS
\#container{
    border: 2px solid;
}
/* \#container p{
    background-color: yellow;
} */
/* \#container > p{
    background-color: yellow;
} */
/* \#container ~ p{
    background-color: yellow;
} */
\#container + p{
    background-color: yellow;
}
```