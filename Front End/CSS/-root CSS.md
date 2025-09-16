---
Created: 2025-06-28T20:42
---
## What is `:root`?

- `:root` is a CSS pseudo-class that matches the highest-level parent in the DOM (for HTML, it’s the `<html>` element).
- It’s the ideal place to define **CSS custom properties (variables)** because their scope will be global.

```CSS
:root {
  --primary-color: \#3498db;
  --secondary-color: \#2ecc71;
  --font-main: 'Helvetica', sans-serif;
}
```

  

## How to Use a CSS Variable

To **declare** a variable:

```CSS
:root {
  --my-color: \#ff6600;
}
```

To **use** a variable:

```CSS
.element {
  color: var(--my-color);
}
```

  

## Basic Syntax

✅ Declaration:

```CSS
--variable-name: value;
```

✅ Usage:

```CSS
property: var(--variable-name);
```

  

## Scope of Variables

- Variables defined in `:root` → **Global** (can be used anywhere).
- Variables defined inside a selector → **Local** (available only inside that selector’s scope).

```CSS
.button {
  --btn-color: \#e74c3c;
  color: var(--btn-color); /* Only within .button */
}
```

  

## Fallback Values

You can provide a fallback if the variable isn’t defined:

```CSS
color: var(--undefined-var, black);
```

  

## Updating Variables with JavaScript

You can dynamically change CSS variables:

```JavaScript
document.documentElement.style.setProperty('--primary-color', '\#8e44ad');
```

  

## Example: Theming with Variables

```CSS
:root {
  --bg-color: white;
  --text-color: black;
}

.dark-theme {
  --bg-color: black;
  --text-color: white;
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
}
```

Then in HTML, toggle theme by adding `.dark-theme` to the body or root element:

```HTML
<body class="dark-theme">
  ...
</body>
```

  

## Why Use CSS Variables?

✅ Centralize design tokens (colors, fonts, spacing).

✅ Easy theming & dark mode.

✅ Dynamic updates via JavaScript.

✅ Reduce repetition & make CSS maintainable.