---
Created: 2025-06-11T18:24
---
## HTML Entities Cheat Sheet

HTML entities let you display **special characters** in your webpage that might otherwise be interpreted as HTML code or are not on your keyboard.

  

### **Common Entities**

|   |   |   |
|---|---|---|
|Entity|Character|Description|
|`&nbsp;`|(space)|Non-breaking space|
|`&lt;`|`<`|Less-than sign|
|`&gt;`|`>`|Greater-than sign|
|`&amp;`|`&`|Ampersand|
|`&quot;`|`"`|Double quotation mark|
|`&apos;`|`'`|Apostrophe (single quote)|
|`&cent;`|¢|Cent sign|
|`&curren;`|¤|Currency sign|
|`&yen;`|¥|Yen sign|
|`&sect;`|§|Section sign|
|`&para;`|¶|Pilcrow (paragraph mark)|
|`&middot;`|·|Middle dot|
|`&bull;`|•|Bullet|

  

### Accented Letters & Letters with Diacritics (Examples)

|   |   |   |
|---|---|---|
|Entity|Character|Description|
|`&Aacute;`|Á|Capital A with acute|
|`&Egrave;`|È|Capital E with grave|
|`&Ntilde;`|Ñ|Capital N with tilde|
|`&Uuml;`|Ü|Capital U with umlaut|
|`&aacute;`|á|Small a with acute|
|`&egrave;`|è|Small e with grave|
|`&ntilde;`|ñ|Small n with tilde|
|`&uuml;`|ü|Small u with umlaut|

  

### **Currency Symbols**

|   |   |   |
|---|---|---|
|Entity|Character|Description|
|`&dollar;`|$|Dollar sign|
|`&euro;`|€|Euro sign|
|`&pound;`|£|Pound sterling|
|`&yen;`|¥|Yen sign|
|`&curren;`|¤|Generic currency sign|

  

### **Mathematical Symbols**

|   |   |   |
|---|---|---|
|Entity|Character|Description|
|`&plus;`|+|Plus sign|
|`&minus;`|−|Minus sign|
|`&times;`|×|Multiplication sign|
|`&divide;`|÷|Division sign|
|`&equals;`|=|Equal sign|
|`&ne;`|≠|Not equal|
|`&le;`|≤|Less than or equal to|
|`&ge;`|≥|Greater than or equal to|
|`&and;`|∧|Logical AND|
|`&or;`|∨|Logical OR|

  

### **Arrows**

|   |   |   |
|---|---|---|
|Entity|Character|Description|
|`&larr;`|←|Left arrow|
|`&rarr;`|→|Right arrow|
|`&uarr;`|↑|Up arrow|
|`&darr;`|↓|Down arrow|
|`&harr;`|↔|Left-right arrow|

  

### **Other Useful Entities**

|   |   |   |
|---|---|---|
|Entity|Character|Description|
|`&copy;`|©|Copyright symbol|
|`&reg;`|®|Registered trademark|
|`&trade;`|™|Trademark|
|`&sect;`|§|Section sign|
|`&dagger;`|†|Dagger|
|`&Dagger;`|‡|Double dagger|
|`&hellip;`|…|Ellipsis (three dots)|

  

### **Numeric Entities**

You can also use **numeric codes**:

|   |   |   |
|---|---|---|
|Code|Character|Description|
|`&#169;` or `&#xA9;`|©|Copyright symbol|
|`&#8364;` or `&#x20AC;`|€|Euro sign|
|`&#38;` or `&#x26;`|&|Ampersand|

  

### Emojis & Unicode Characters

While HTML entities exist for many emojis, it’s usually easier to use the actual emoji character directly or Unicode escapes.

|   |   |   |
|---|---|---|
|Emoji|Unicode Codepoint|Entity (rarely used)|
|😀 Grinning Face|U+1F600|`&#128512;`|
|❤️ Red Heart|U+2764|`&#10084;`|
|👍 Thumbs Up|U+1F44D|`&#128077;`|
|🎉 Party Popper|U+1F389|`&#127881;`|
|🚀 Rocket|U+1F680|`&#128640;`|

  

### Summary

- Use **named entities** like `&amp;` or numeric like `&#38;` to show reserved characters safely.
- Non-breaking space `&nbsp;` is useful for keeping words together.
- Always encode special characters when outputting user-generated content to prevent HTML injection.