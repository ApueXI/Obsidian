---
Created: 2025-06-11T17:24
---
## CSS Media Queries Cheat Sheet

Media queries let your site **respond to different screen sizes and device features**.

### **Basic Syntax**

```CSS
@media (condition) {
  /* CSS rules */
}
```

  

### **Common Conditions**

|   |   |
|---|---|
|Condition|Meaning|
|`max-width: 768px`|Styles apply up to 768px wide screens|
|`min-width: 769px`|Styles apply for screens wider than 768px|
|`orientation: portrait`|Screen is in portrait mode|
|`orientation: landscape`|Screen is in landscape mode|
|`prefers-color-scheme: dark`|User prefers dark mode|

  

### **Examples**

### a. For Mobile Devices (small screens)

```CSS
@media (max-width: 600px) {
  body {
    background-color: lightyellow;
  }
}
```

### b. For Tablets and Larger Screens

```CSS
@media (min-width: 601px) and (max-width: 1024px) {
  body {
    background-color: lightgreen;
  }
}
```

### c. Dark Mode Preference

```CSS
@media (prefers-color-scheme: dark) {
  body {
    background-color: black;
    color: white;
  }
}
```

  

### **Targeting Multiple Features**

```CSS
@media (min-width: 600px) and (orientation: landscape) {
  /* Landscape tablets and up */
}
```

  

### **Using Media Queries in HTML (Legacy)**

```HTML
<link rel="stylesheet" media="(max-width: 600px)" href="mobile.css">
```

  

### Summary Table

|   |   |
|---|---|
|Media Feature|Description|
|`width`, `height`|Viewport size|
|`min-width`, `max-width`|Minimum/maximum viewport width|
|`orientation`|Portrait or landscape|
|`resolution`|Screen DPI or pixel density|
|`prefers-color-scheme`|Dark or light mode|
|`aspect-ratio`|Width-to-height ratio|

  

### Summary Table

|   |   |
|---|---|
|Media Feature|Description|
|`width`, `height`|Viewport size|
|`min-width`, `max-width`|Minimum/maximum viewport width|
|`orientation`|Portrait or landscape|
|`resolution`|Screen DPI or pixel density|
|`prefers-color-scheme`|Dark or light mode|
|`aspect-ratio`|Width-to-height ratio|