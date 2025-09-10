---
Created: 2025-06-23T18:55
---
## What is Semantic HTML?

- Using HTML elements that **describe their meaning clearly** both to the browser and developers.
- Improves **accessibility**, **SEO**, and code **readability**.

  

## Common Semantic Elements & Their Purpose

|   |   |   |
|---|---|---|
|Element|Purpose|Example Use Case|
|`<header>`|Introductory content or site header|Site logo, navigation menu|
|`<nav>`|Navigation links|Main menu, sidebar links|
|`<main>`|Main content of the document|Blog posts, articles, primary content|
|`<section>`|Thematic grouping of content|Chapters, tab contents|
|`<article>`|Independent, self-contained content|Blog post, news article|
|`<aside>`|Sidebar or tangential content|Related links, ads, quotes|
|`<footer>`|Footer content for section or page|Copyright info, contact links|
|`<figure>`|Self-contained content with media + caption|Images, diagrams, code snippets|
|`<figcaption>`|Caption for `<figure>`|Describes the figure|
|`<mark>`|Highlighted text|Marking keywords or important notes|
|`<time>`|Date/time information|Publish date, event time|

  

## Benefits of Semantic HTML

- **Improves SEO**: Search engines understand page structure better.
- **Accessibility**: Screen readers and assistive tech navigate easily.
- **Better maintainability**: Code is easier to read and manage.
- **Consistent styling hooks**: Target elements more precisely with CSS.

  

## Non-semantic vs Semantic Example

### Non-semantic:

```HTML
<div id="header">...</div>
<div class="nav">...</div>
<div id="content">...</div>
<div id="footer">...</div>
```

### Semantic:

```HTML
<header>...</header>
<nav>...</nav>
<main>...</main>
<footer>...</footer>
```