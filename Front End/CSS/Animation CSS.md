---
Created: 2025-06-12T20:34
---
### Basic Syntax

```CSS
selector {
  animation: name duration timing-function delay iteration-count direction fill-mode;
}
```

```CSS
.box {
  animation: slide 2s ease-in-out 0s infinite alternate forwards;
}
```

  

### @keyframes (Define Animation)

```CSS
@keyframes slide {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(100px);
  }
}
```

Or use percentages:

```CSS
@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}
```

  

### Animation Properties

|   |   |   |
|---|---|---|
|Property|Description|Example|
|`animation-name`|Name of the keyframes|`slide`|
|`animation-duration`|How long it runs|`2s`, `500ms`|
|`animation-timing-function`|Easing style|`linear`, `ease-in`, `ease-out`, `ease-in-out`, `cubic-bezier(...)`|
|`animation-delay`|Wait before starting|`1s`|
|`animation-iteration-count`|How many times|`1`, `infinite`, `3`|
|`animation-direction`|Direction|`normal`, `reverse`, `alternate`, `alternate-reverse`|
|`animation-fill-mode`|Keep final state|`none`, `forwards`, `backwards`, `both`|
|`animation-play-state`|Pause or play|`running`, `paused`|

  

### Shorthand Example

```CSS
.box {
  animation: bounce 1s infinite alternate ease-in-out;
}
```

  

### Common Animation Examples

### Bounce

```CSS
@keyframes bounce {
  0% { transform: translateY(0); }
  50% { transform: translateY(-30px); }
  100% { transform: translateY(0); }
}
```

### Fade In

```CSS
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
```

### Slide In Left

```CSS
@keyframes slideInLeft {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(0); }
}
```

  

### Trigger with Hover

```CSS
.box:hover {
  animation: wiggle 0.5s ease-in-out;
}
```

  

### Tips

- Combine `transform`, `opacity`, and `color` for creative effects.
- Use `will-change` for performance boost in complex animations:

```CSS
.box {
  will-change: transform, opacity;
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Animation.css">
    <title>Animation</title>
</head>
<body>
    
    <div id="box">HI</div>

</body>
</html>
```

```CSS
body {
    background-color: black;
}

\#box {
    width: 250px;
    height: 250px;
    background-color: red;
    font-size: 13em;
    text-align: center;
    animation-name: color;
    animation-duration: 5s;
    animation-iteration-count: infinite;
    animation-direction: alternate-reverse;
    animation-timing-function: linear;
}

\#box:hover {
    animation-name: glow, color;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
}

@keyframes slideleft {
    from {
        transform: translateX(100%);
    }
}

@keyframes slideright {
    to {
        transform: translateX(300%);
    }
}

@keyframes slideup {
    from {
        transform: translateY(300%);
    }
}

@keyframes slidedown {
    to {
        transform: translateY(300%);
    }
}

@keyframes rotate {
    0% {
        transform: scale(1);
    }

    50% {
        transform: scale(1.2);
    }

    100% {
        transform: scale(1);
    }
}

@keyframes grow {
    100% {
        transform: scale(2, 2);
    }
}

@keyframes shrink {
    100% {
        transform: scale(0.5, 0.5);
    }
}

@keyframes fade {
    50% {
        opacity: 0;
    }
}

@keyframes color {
    0% {
        background-color: red;
    }

    20% {
        background-color: orange;
    }

    40% {
        background-color: yellow;
    }

    60% {
        background-color: green;
    }

    80% {
        background-color: blue;
    }

    100% {
        background-color: violet;
    }
}

@keyframes glow {
    50% {
        box-shadow: 10px 10px 50px yellowgreen;
    }
}
```