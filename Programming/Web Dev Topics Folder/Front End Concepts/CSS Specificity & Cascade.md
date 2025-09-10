---
Created: 2025-06-23T19:00
---
## What is CSS Specificity?

- A weight that determines **which CSS rule applies** when multiple rules target the same element.
- Calculated based on the selectors used.

  

## Specificity Hierarchy (Highest to Lowest)

|   |   |   |
|---|---|---|
|Selector Type|Specificity Value|Example|
|Inline styles|1,0,0,0|`<div style="color:red">`|
|ID selectors|0,1,0,0|`#header`|
|Class, attribute, pseudo-class selectors|0,0,1,0|`.menu`, `[type="text"]`, `:hover`|
|Element and pseudo-element selectors|0,0,0,1|`div`, `p`, `::before`|
|Universal selector (`*`), combinators (`+`, `>`, `~`)|0,0,0,0|`*`, `div > p` (do not add specificity)|

  

## Specificity Calculation Example

Selector:

```CSS
\#nav ul.menu > li.active a:hover
```

Specificity Breakdown:

- `#nav` → ID → 0,1,0,0
- `ul.menu` → element + class → 0,0,1,1
- `li.active` → element + class → 0,0,1,1
- `a:hover` → element + pseudo-class → 0,0,1,1

Add up: 0,1,3,3

  

## CSS Cascade Order (Which rule wins?)

1. **Important rules:** `!important` overrides everything else.
2. **Inline styles:** highest specificity after `!important`.
3. **IDs:** higher specificity than classes.
4. **Classes, attributes, pseudo-classes:** moderate specificity.
5. **Elements and pseudo-elements:** lowest specificity.
6. **Source order:** If specificity is equal, later rules override earlier ones.

  

## `!important`

- Overrides normal specificity and cascade.
- Use sparingly to avoid difficulty in debugging.
- `!important` on inline styles beats `!important` in external stylesheets only if inline comes later.

  

## Inheritance

- Some properties inherit values from their parent elements (e.g., `color`, `font-family`).
- Others do not (e.g., `margin`, `padding`).

  

## Summary Table

|   |   |   |
|---|---|---|
|Selector|Specificity Score|Notes|
|Inline style|1000|`style=""` attribute|
|ID selector|100|`#id`|
|Class/attribute/pseudo-class|10|`.class`, `[attr=value]`, `:hover`|
|Element/pseudo-element|1|`div`, `p`, `::before`|

  

## Tips

- Avoid overusing IDs for styling (hard to override).
- Use classes for reusable styling.
- Use `!important` only when necessary.
- Remember that order matters when specificity is the same.