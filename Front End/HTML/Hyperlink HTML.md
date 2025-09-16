---
Created: 2025-06-06T10:10
---
## ==What Is a Hyperlink in HTML?==

A **hyperlink** lets you **link from one page to another**, or to a different section, file, email, or website.

  

## **Basic Anchor Tag**

```HTML
<a href="https://example.com">Visit Example</a>
```

- `<a>` is the **anchor element**.
- `href` is the **destination URL**.
- The text between the tags is **clickable**.

  

## **Link Types by** `**href**`

|   |   |   |
|---|---|---|
|Type|Example|Description|
|Absolute URL|`href="https://google.com"`|Link to another website|
|Relative URL|`href="/about.html"`|Link to another file in your site|
|Section on same page|`href="#top"`|Scroll to a page section with an ID|
|File download|`href="file.pdf"`|Link to a downloadable file|
|Email|`href="mailto:someone@example.com"`|Opens default mail app|
|Phone number|`href="tel:+123456789"`|Click to call (mobile devices)|

## **Target Attribute**

```HTML
<a href="page.html" target="_blank">Open in New Tab</a>
```

|   |   |
|---|---|
|Value|Description|
|`_self` (default)|Open in same tab|
|`_blank`|Open in new tab/window|
|`_parent`|Open in parent frame|
|`_top`|Open in full body of window|

## **Other Common Attributes**

|   |   |   |
|---|---|---|
|Attribute|Description|Example|
|`title`|Tooltip on hover|`title="Click to visit"`|
|`download`|Force download|`download="file.pdf"`|
|`rel`|Relationship hint|`rel="noopener noreferrer"` (used with `target="_blank"` for security)|
|`id`|Used to link to a specific part of a page|`<div id="section1">...</div>` + `<a href="#section1">Jump</a>`|

  

## **Linking to Sections on the Same Page**

```HTML
<a href="\#contact">Go to Contact</a>

<!-- later on the page -->
<div id="contact">Contact Section</div>
```

  

## **Download Link Example**

```HTML
<a href="ebook.pdf" download>Download PDF</a>
```

  

## **Email & Phone Links**

```HTML
<a href="mailto:info@example.com">Email Us</a>
<a href="tel:+15555555555">Call Now</a>
```

  

## **Clickable Image Link**

```HTML
<a href="https://example.com">
  <img src="logo.png" alt="Example Logo">
</a>
```

  

## **Button-Like Link (Styled)**

```HTML
<a href="contact.html" class="btn">Contact Us</a>
<style>
.btn {
  padding: 10px 20px;
  background: blue;
  color: white;
  text-decoration: none;
  border-radius: 5px;
}

</style>
```

  

## **Security Tip with** `**_blank**`

When using `target="_blank"`, always add `rel="noopener noreferrer"`:

```HTML
<a href="https://example.com" target="_blank" rel="noopener noreferrer">Secure Link</a>
```

This prevents a security risk called **tab-nabbing**.

  

## Summary of Key Tags and Attributes

|   |   |
|---|---|
|Element / Attribute|Purpose|
|`<a>`|Defines a hyperlink|
|`href`|URL or destination|
|`target`|Where to open (e.g., `_blank`)|
|`title`|Tooltip text|
|`download`|Initiates file download|
|`rel`|Defines relationship / security hints|
|`mailto:` / `tel:`|Email or phone link|

  

target - decides whether to enter a new tab or current tab to open the link

mailto:@gmail.com - mailts to a gmail

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hyperlink</title>
</head>

<body>
    <a href="https://x.com/home" target="_blank" title="Goes to Google">
        click me
    </a>
    <br>
    <a href="basics.html" target="_blank" title="Goes to other html file">
        goes to basics html
    </a>
    <br>
    <a href="mailto:test@fake@gmail.com">
        send email
    </a>
</body>

</html>
```