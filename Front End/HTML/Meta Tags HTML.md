---
Created: 2025-06-11T18:19
---
## HTML Meta Tags Cheat Sheet

Meta tags go inside the `<head>` and give browsers & services important info about your page.

  

### **Basic Meta Tags**

```HTML
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

|   |   |
|---|---|
|Tag|Purpose|
|`charset`|Sets character encoding (UTF-8 recommended)|
|`viewport`|Controls layout on mobile devices (responsive design)|
|`X-UA-Compatible`|Ensures IE uses the latest rendering engine|

  

### **SEO Meta Tags**

```HTML
<meta name="description" content="A comprehensive guide to CSS and HTML cheat sheets.">
<meta name="keywords" content="HTML, CSS, cheat sheet, web development">
<meta name="author" content="Your Name">
```

- `description`: Shown in search results snippet
- `keywords`: Mostly ignored by modern search engines but still used sometimes
- `author`: Page or site creator

  

### **Social Media (Open Graph & Twitter Cards)**

```HTML
<!-- Open Graph for Facebook, LinkedIn -->
<meta property="og:title" content="CSS & HTML Cheat Sheets">
<meta property="og:description" content="Your go-to resource for web development cheat sheets.">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="CSS & HTML Cheat Sheets">
<meta name="twitter:description" content="Your go-to resource for web development cheat sheets.">
<meta name="twitter:image" content="https://example.com/image.jpg">
```

  

### **Other Useful Meta Tags**

|   |   |
|---|---|
|Tag|Purpose|
|`<meta http-equiv="refresh" content="30">`|Refresh page every 30 seconds|
|`<meta name="robots" content="index, follow">`|Controls if search engines index or follow links|
|`<meta name="theme-color" content="#317EFB">`|Sets browser toolbar color on mobile|

  

### Summary Table

|   |   |
|---|---|
|Meta Tag|Usage|
|`charset`|Define character encoding|
|`viewport`|Responsive layout control|
|`description`|SEO snippet|
|`keywords`|Keywords for SEO (less used now)|
|`author`|Author of the document|
|`og:*`|Social sharing metadata|
|`twitter:*`|Twitter card metadata|