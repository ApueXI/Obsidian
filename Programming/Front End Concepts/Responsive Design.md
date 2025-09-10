---
Created: 2025-06-23T19:01
---
## What is Responsive Design?

- Designing web pages that **adapt smoothly** to different screen sizes and devices (mobile, tablet, desktop).
- Provides optimal user experience **regardless of device**.

  

## Key Techniques

|   |   |   |
|---|---|---|
|Technique|Description|Example|
|**Fluid Grids**|Layout uses relative units (`%`, `vw`) instead of fixed pixels|`width: 80%;`|
|**Flexible Images**|Images scale within containers|`max-width: 100%; height: auto;`|
|**Media Queries**|Apply CSS rules based on screen size or features|`@media (max-width: 768px) { ... }`|
|**Viewport Meta Tag**|Controls layout on mobile browsers|`<meta name="viewport" content="width=device-width, initial-scale=1">`|
|**Responsive Typography**|Text scales for readability|`font-size: clamp(1rem, 2vw, 2rem);`|

  

## Common Media Query Breakpoints

|   |   |
|---|---|
|Device Type|Typical Max Width|
|Mobile (phones)|480px|
|Tablets|768px|
|Laptops|1024px|
|Desktops|1200px and above|

  

## Sample Media Query

```CSS
/* For screens smaller than 768px (tablets and below) */
@media (max-width: 768px) {
  body {
    background-color: lightgray;
  }
  nav {
    display: none;
  }
}
```

  

## Tips for Responsive Design

- Start with **mobile-first** CSS, then add styles for larger screens.
- Use **flexbox** and **CSS grid** for flexible layouts.
- Test on real devices or device simulators.
- Optimize images for different screen sizes.
- Avoid fixed widths and heights; prefer relative units.