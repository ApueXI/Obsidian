---
Created: 2025-06-11T17:18
---
## HTML `<iframe>` Cheat Sheet

An `**<iframe>**` **(inline frame)** lets you embed another webpage, document, or media inside your current HTML page.

  

## **Basic Syntax**

```HTML
<iframe src="https://example.com"></iframe>
```

|   |   |
|---|---|
|Attribute|Description|
|`src`|The URL of the page to embed|

  

## **Common Attributes**

```HTML
<iframe src="https://example.com"
  width="600"
  height="400"
  title="Descriptive text"
  loading="lazy"
  frameborder="0"
  allowfullscreen>
</iframe>
```

|   |   |
|---|---|
|Attribute|Purpose|
|`width` / `height`|Size in pixels or %|
|`title`|Accessibility: screen readers use this|
|`loading="lazy"`|Loads iframe only when needed|
|`frameborder="0"`|Removes the default border (deprecated, use CSS)|
|`allowfullscreen`|Allows full screen for embedded media|

## **CSS Styling Example**

```CSS
iframe {
  border: none;
  border-radius: 8px;
  max-width: 100%;
}
```

  

## **Embedding YouTube Video with** `**<iframe>**`

```HTML
<iframe width="560"
  height="315"
  src="https://www.youtube.com/embed/dQw4w9WgXcQ"
  title="YouTube video player"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>
```

  

## **Responsive Iframe (CSS Trick)**

```HTML
<div class="iframe-container">
  <iframe src="https://example.com"></iframe>
</div>

<style>
.iframe-container {
  position: relative;
  padding-top: 56.25%; /* 16:9 ratio */
  height: 0;
  overflow: hidden;
}
.iframe-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 0;
}
</style>
```

  

## **Security Note: Sandbox Attribute**

```HTML
<iframe src="page.html" sandbox></iframe>
```

- Restricts what the iframe can do
- Can allow specific permissions:

```HTML
<iframe src="page.html" sandbox="allow-scripts allow-forms"></iframe>
```

|   |   |
|---|---|
|Sandbox Option|Effect|
|`allow-scripts`|Run JS in iframe|
|`allow-forms`|Allow form submission|
|`allow-same-origin`|Treat iframe as same origin|
|`allow-popups`|Allow popups|

  

## Summary Table

|   |   |
|---|---|
|Element|Use|
|`<iframe>`|Embed pages, videos, maps, etc.|
|`src`|Source URL|
|`title`|For accessibility|
|`loading`|Lazy loading option|
|`sandbox`|Restrict iframe permissions|
|`allowfullscreen`|Allow full screen (e.g., for YouTube)|