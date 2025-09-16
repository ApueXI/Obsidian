---
Created: 2025-06-09T21:02
---
position:

relative = positioned relative to where it normally

fixed = positioned relative to the viewport

absolute = positioned relative to nearest ancestor

sticky = positioned based on scroll position

static = default position for an element

  

## `position` – How Elements Are Positioned

```CSS
position: static | relative | absolute | fixed | sticky;
```

  

## Position Values Explained

|   |   |
|---|---|
|Value|Description|
|`static`|Default. Element flows normally in the document (no positioning).|
|`relative`|Positioned relative to its **normal position**. Offsets (top, left, etc.) move it from there.|
|`absolute`|Positioned relative to the **nearest positioned ancestor** (non-static). Removed from normal flow.|
|`fixed`|Positioned relative to the **viewport**. Stays fixed on screen even when scrolling. Removed from flow.|
|`sticky`|Acts like `relative` until a scroll threshold is reached, then behaves like `fixed`.|

  

## Position Offsets

|   |   |
|---|---|
|Property|What it does|
|`top`|Distance from the top edge of the containing block or viewport|
|`right`|Distance from the right edge|
|`bottom`|Distance from the bottom edge|
|`left`|Distance from the left edge|

  

## How Positioning Works

|   |   |   |
|---|---|---|
|Position|Layout Impact|Reference Point|
|`static`|In normal flow|N/A|
|`relative`|Leaves space, moves visually|Its own original spot|
|`absolute`|Removed from flow|Closest positioned ancestor or `html`|
|`fixed`|Removed from flow|Viewport|
|`sticky`|Switches between flow & fixed|Depends on scroll position|

  

## Example Usage

```CSS
/* Relative */
.relative-box {
  position: relative;
  top: 10px;   /* Moves down 10px from original spot */
  left: 20px;  /* Moves right 20px */
}

/* Absolute */
.absolute-box {
  position: absolute;
  top: 0;
  right: 0;
}

/* Fixed */
.fixed-box {
  position: fixed;
  bottom: 10px;
  left: 10px;
}

/* Sticky */
.sticky-box {
  position: sticky;
  top: 0;  /* Sticks to top of viewport when scrolling */
}
```

  

## Positioning Context (Containing Block)

- For `absolute`, the element positions itself relative to the **nearest ancestor** with `position` **not static**.
- If none, it positions relative to the viewport/document root.
- For `sticky`, the parent must have a height for it to work properly.

  

## Common Use Cases

|   |   |
|---|---|
|Use Case|Position Type|
|Normal flow content|`static` (default)|
|Slight offset without removing from flow|`relative`|
|Tooltip/popups|`absolute`|
|Fixed headers/footers|`fixed`|
|Sticky navbar on scroll|`sticky`|

  

## Bonus: Z-Index

```CSS
.element {
  position: relative; /* or absolute, fixed, sticky */
  z-index: 10;        /* Higher number = on top */
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Positions.css">
    <title>Positions</title>
</head>

<body>

    <div id="box1">
        <div id="box2">
            
        </div>
    </div>

    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas rerum sit exercitationem quam temporibus vitae
        numquam porro molestias placeat, ea adipisci ex. In dicta, eos aspernatur error ullam impedit veritatis!</p>
    <p>Tenetur, quaerat laboriosam. Et incidunt, vel ullam culpa vero quibusdam molestiae laboriosam laborum explicabo
        impedit fugiat voluptas veritatis, aperiam voluptates aliquid debitis? Nihil velit dignissimos quia doloribus,
        architecto asperiores sapiente.</p>
    <p>Iure nesciunt reprehenderit error quia sunt saepe illum minima inventore eaque natus, ex excepturi earum
        molestiae quaerat, veniam enim ipsa laudantium similique quasi quos. Non omnis veniam sed iusto consectetur.</p>
    <p>Eveniet eius tenetur non tempore alias minus! Soluta magnam beatae nobis sed voluptate consectetur sapiente fuga
        necessitatibus laboriosam impedit accusantium debitis illum error eius nemo voluptas quis, hic adipisci dolores.
    </p>
    <p>Neque sed aspernatur ipsam nam dolor minus porro, obcaecati laboriosam dolorum ad esse soluta autem, harum
        laudantium, amet itaque vitae non nobis. Assumenda cumque culpa voluptates itaque quae, dolore quas.</p>
    <p>Deserunt reprehenderit doloremque deleniti reiciendis dolores error quod veniam quis quae, unde nobis alias vero
        atque voluptatum! Soluta harum obcaecati voluptates culpa beatae provident saepe nobis repellendus quo, suscipit
        labore.</p>
    <p>Natus, illum fugiat. Unde cumque, omnis dolorum repudiandae nostrum atque molestiae perspiciatis aspernatur!
        Soluta recusandae tempora, natus aliquam voluptas nihil nam quas necessitatibus. Aliquam explicabo, mollitia
        reiciendis vero non maiores.</p>
    <p>Quas qui, possimus sed aliquid, quod alias culpa impedit repellat nisi accusantium ab sit quidem ipsum quo
        asperiores natus repellendus nam consectetur labore unde blanditiis facilis recusandae. Est, magni dicta.</p>
    <p>Quod minus quam distinctio? Dolor neque consectetur reprehenderit deleniti praesentium molestias facere quis
        magni sint obcaecati sunt dolorum dignissimos totam, ea similique? Harum, delectus dicta! Ab necessitatibus
        eaque delectus reiciendis.</p>
    <p>Autem fugit eos ratione velit minima libero reiciendis architecto praesentium, eveniet vero, expedita aliquam
        minus, animi dolores soluta provident nihil suscipit adipisci! Nihil vel aut aliquid accusamus excepturi nisi
        earum!</p>
    <p>Non totam distinctio perspiciatis nesciunt rem, amet dolores, exercitationem incidunt fugiat quod enim iusto
        illum ducimus ipsam ab tenetur dicta asperiores at maxime, quam voluptatem voluptatum sint nam? Debitis,
        incidunt.</p>
    <p>Ullam tempore autem error dolor? Blanditiis, neque dolorum numquam eum corrupti animi veritatis dicta libero,
        obcaecati necessitatibus beatae quos aperiam molestias vero. Soluta eveniet repellendus debitis modi quae
        perferendis ipsam?</p>
    <p>Soluta impedit amet sit! Iure esse, ipsa est totam ratione fuga vero, dignissimos doloremque sed accusamus amet
        quos facilis dolorum! Officiis ipsa odio incidunt nisi, vero quas nulla. Quidem, officiis.</p>
    <p>Commodi non in provident autem minus ipsam consectetur facere ab ut deserunt similique asperiores inventore nulla
        ea, qui facilis reiciendis ad sed. Asperiores, soluta dignissimos sint aspernatur alias repellendus expedita.
    </p>
    <p>Laboriosam minus voluptates, impedit, suscipit iure velit est et officia eius porro natus tenetur ullam maiores.
        Ipsum modi corrupti minus eum quia iure doloribus tenetur vitae dignissimos aliquid, expedita natus.</p>
    <p>Necessitatibus molestias magni deserunt. Laudantium impedit corporis facere hic sapiente corrupti, a est magnam
        at expedita nostrum. Soluta exercitationem error numquam rem optio molestias. Sed veniam in facilis error
        nesciunt.</p>
    <p>Expedita, sequi repellendus corporis distinctio officiis atque asperiores similique aliquid culpa, non ratione
        libero, ipsam consequatur architecto! Unde repudiandae ab, error nam delectus non ut! Sed provident aspernatur
        ipsam reiciendis.</p>
    <p>Perferendis quibusdam expedita molestias ad nostrum repudiandae. Alias, ratione! Doloribus aperiam nesciunt
        incidunt, repudiandae reiciendis itaque, rerum dolore temporibus iure culpa labore asperiores unde fuga quas
        necessitatibus consectetur neque libero!</p>
    <p>Excepturi blanditiis magni quasi pariatur laborum accusamus quibusdam deserunt! Exercitationem inventore esse
        mollitia, quaerat voluptate sed dolor tempora. Aperiam unde, fugit quibusdam maxime ipsa quas? Sed, iusto. A,
        quidem labore!</p>
    <p>Odit quaerat temporibus repellendus assumenda in perspiciatis quae id iste, odio enim eveniet est officiis
        aliquam debitis praesentium, maiores minus aliquid ad placeat eius quo. Omnis in modi maxime dignissimos.</p>

</body>

</html>
```

```CSS
\#box1{
    width: 200px;
    height: 200px;
    background-color: blue;
    position: sticky;
    top: 0px;
}
\#box2{
    width: 100px;
    height: 100px;
    background-color: red;
    position: absolute;
    top: 25%;
    left: 25%;
}
```