---
Created: 2025-06-23T18:58
---
## What is Accessibility (a11y)?

- Designing websites/apps so **everyone**, including people with disabilities, can use them.
- "a11y" = abbreviation of “accessibility” (11 letters omitted).

  

## Why It Matters

- Legal requirements in many countries.
- Improves user experience for all users.
- Helps users with visual, auditory, motor, or cognitive impairments.
- Boosts SEO and site reach.

  

## Core Principles ( POUR )

|   |   |
|---|---|
|Principle|Description|
|**Perceivable**|Info must be presented so users can perceive it (e.g., text alternatives for images)|
|**Operable**|Interface must be usable by everyone (keyboard navigation, no traps)|
|**Understandable**|Content and UI must be clear and simple to understand|
|**Robust**|Content must work reliably across different devices and assistive technologies|

  

## Common Accessibility Features & Tips

|   |   |
|---|---|
|Feature / Attribute|Purpose / Usage|
|**Alt text (**`**alt**`**)**|Describe images for screen readers|
|**ARIA roles & labels**|Provide semantic info to assistive tech (e.g., `role="button"`, `aria-label="Close"`)|
|**Keyboard navigation**|Ensure all interactive elements work with keyboard (Tab, Enter, Space)|
|**Focus management**|Visible focus indicators (`:focus` styles)|
|**Contrast ratio**|Text/background contrast at least 4.5:1|
|**Labels & form controls**|Use `<label>` linked to form inputs|
|**Skip links**|Allow users to skip repetitive content|
|**Headings hierarchy**|Use proper heading order (`<h1>` to `<h6>`)|
|**Avoid auto-playing media**|Can disrupt assistive tech users|
|**Use semantic HTML**|Helps assistive devices understand content|

  

## Testing Tools & Techniques

- **Screen readers:** NVDA, VoiceOver, JAWS
- **Browser extensions:** Axe, WAVE, Lighthouse
- **Keyboard only testing:** Navigate without mouse
- **Color contrast checkers:** WebAIM Contrast Checker

  

## Quick Accessibility Checklist

- Images have descriptive alt text
- Interactive elements accessible via keyboard
- Forms have associated labels
- Sufficient color contrast
- Clear and logical heading structure
- ARIA attributes used appropriately
- No content that flashes rapidly
- Skip navigation links present