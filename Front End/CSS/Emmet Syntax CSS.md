---
Created: 2025-06-11T19:28
---
### Selectors

|   |   |
|---|---|
|Selector|Description|
|`*`|Universal selector (targets all elements)|
|`element`|Targets specific elements like `p`, `h1`, `div`|
|`#id`|Targets element with specific ID|
|`.class`|Targets elements with a specific class|
|`element, element2`|Grouping multiple selectors|
|`element element2`|Descendant selector|
|`element > element2`|Direct child selector|
|`element + element2`|Adjacent sibling|
|`element ~ element2`|General sibling|
|`[attr]`|Attribute selector|
|`[attr="value"]`|Attribute = value|

  

### 🎨 Color & Background

|   |   |
|---|---|
|Property|Description|
|`color`|Text color|
|`background-color`|Background color|
|`background-image`|Set image background|
|`background-size`|Cover, contain, auto, px|
|`background-repeat`|Repeat or no-repeat|
|`background-position`|Position image (top, center, etc.)|

  

### Box Model

|   |   |
|---|---|
|Property|Description|
|`margin`|Outer spacing|
|`padding`|Inner spacing|
|`border`|Border of the element|
|`width` / `height`|Size of the box|
|`box-sizing`|`content-box` or `border-box`|

  

### Positioning

|   |   |
|---|---|
|Property|Values|
|`position`|`static`, `relative`, `absolute`, `fixed`, `sticky`|
|`top`, `right`, `bottom`, `left`|Offsets (when position is set)|
|`z-index`|Layer order|

  

### Display & Flexbox

|   |   |
|---|---|
|Property|Description|
|`display`|`block`, `inline`, `inline-block`, `flex`, `grid`, `none`|
|`flex-direction`|`row`, `column`|
|`justify-content`|Aligns horizontally|
|`align-items`|Aligns vertically|
|`gap`|Spacing between flex items|

  

### Grid (Basics)

|   |   |
|---|---|
|Property|Description|
|`display: grid`|Enables grid layout|
|`grid-template-columns`|Set column layout|
|`grid-template-rows`|Set row layout|
|`gap`|Space between grid items|
|`grid-column`, `grid-row`|Span grid items|

  

### Text & Font

|   |   |
|---|---|
|Property|Description|
|`font-family`|Font type|
|`font-size`|Font size|
|`font-weight`|Normal, bold, etc.|
|`line-height`|Space between lines|
|`text-align`|Left, right, center, justify|
|`text-decoration`|Underline, none, etc.|
|`text-transform`|Capitalize, uppercase, lowercase|

  

### Effects & Visibility

|   |   |
|---|---|
|Property|Description|
|`opacity`|Transparency (0–1)|
|`box-shadow`|Add shadow to element|
|`text-shadow`|Add shadow to text|
|`visibility`|`visible`, `hidden`|
|`overflow`|`visible`, `hidden`, `scroll`, `auto`|

  

### Effects & Visibility

|   |   |
|---|---|
|Property|Description|
|`opacity`|Transparency (0–1)|
|`box-shadow`|Add shadow to element|
|`text-shadow`|Add shadow to text|
|`visibility`|`visible`, `hidden`|
|`overflow`|`visible`, `hidden`, `scroll`, `auto`|

  

### Transitions & Animations

|   |   |
|---|---|
|Property|Description|
|`transition`|Add smooth effect|
|`animation`|Trigger animations|
|`@keyframes`|Define animation steps|

  

### Media Queries

```CSS
@media (max-width: 768px) {
  /* Responsive styles here */
}
```

  

### Pseudo-classes

|   |   |
|---|---|
|Syntax|Description|
|`:hover`|On hover|
|`:active`|On click|
|`:focus`|When focused|
|`:first-child`|First of siblings|
|`:nth-child(2)`|Specific child|

  

### Pseudo-elements

|   |   |
|---|---|
|Syntax|Description|
|`::before`|Content before element|
|`::after`|Content after element|
|`::placeholder`|Placeholder styling|

  

### Other Useful Properties

|   |   |
|---|---|
|Property|Description|
|`cursor`|Mouse cursor style|
|`list-style`|Customize list bullets|
|`visibility`|Hide/show elements without layout change|
|`pointer-events`|Enable/disable click behavior|