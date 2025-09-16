---
Created: 2025-06-09T11:40
---
overflow = property that sets the desired behavior when content does not fit in the parent element box (overflows)

  
overflow: visible  
overflow: hidden  
overflow: clip  
overflow: scroll  
overflow: auto

  

## `overflow` – Controls What Happens When Content Overflows

```CSS
overflow: visible | hidden | scroll | auto | clip;
```

  

  
Common `overflow` Values

|   |   |
|---|---|
|Value|Description|
|`visible` (default)|Content spills **outside** the box — no clipping.|
|`hidden`|**Clips** content that overflows — no scrollbars.|
|`scroll`|Always shows **scrollbars**, even if not needed.|
|`auto`|Shows **scrollbars only when needed**.|
|`clip`|Clips the content like `hidden`, but can't scroll to it.|

  

```CSS
div {
  width: 200px;
  height: 100px;
  overflow: auto;
}
```

  

## `overflow-x` & `overflow-y` – Control Axes Separately

|   |   |
|---|---|
|Property|Description|
|`overflow-x`|Controls horizontal overflow|
|`overflow-y`|Controls vertical overflow|

```CSS
overflow-x: auto;
overflow-y: hidden;
```

  

## Scrollable Content Example

```HTML
<div style="width: 300px; height: 100px; overflow: auto;">
  <p>This is a long paragraph that will scroll inside the div if it overflows the box dimensions.</p>
</div>
```

  

## `clip` vs `hidden`

|   |   |   |
|---|---|---|
|Property|Scroll?|Clipping?|
|`hidden`|❌ No|✅ Yes|
|`clip`|❌ No|✅ Yes (Newer, stricter than `hidden`)|

  

## Advanced: `overflow: clip` + `text-overflow`

To make **text truncate with ellipsis (**`**...**`**)**:

```CSS
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
```

  

## Summary Quick Table

|   |   |   |
|---|---|---|
|Value|Content Visible?|Scrollable?|
|`visible`|✅ Yes|❌ No|
|`hidden`|❌ No|❌ No|
|`scroll`|✅ Yes|✅ Always|
|`auto`|✅ When Needed|✅ When Needed|
|`clip`|❌ No|❌ No|

  

  

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=], initial-scale=1.0">
    <link rel="stylesheet" href="Overflow.css">
    <title>Overflow</title>
</head>

<body>

    <div id="divs">
        <p id="p1">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Hic obcaecati possimus, corporis laborum
            iste omnis consequatur fuga harum, impedit repellendus asperiores temporibus at dignissimos veniam expedita
            exercitationem sit, ab deleniti!
        </p>
    </div>

</body>

</html>
```

```CSS
\#divs {
    border: 2px solid;
    height: 75px;
    overflow: scroll;
}
/* \#divs {
    border: 2px solid;
    height: 75px;
    overflow: clip;
    overflow-clip-margin: 10px;
} */
```