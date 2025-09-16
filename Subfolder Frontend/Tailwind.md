
> [!important]
> 
> ### ==[https://tailwindcss.com/docs/installation/using-vite](https://tailwindcss.com/docs/installation/using-vite)==
> 
> ### ==[https://tailwindcss.com/](https://tailwindcss.com/)==
> 
> ### ==[https://v2.tailwindcss.com/docs](https://v2.tailwindcss.com/docs)==
> 
> ### ==[https://www.creative-tim.com/twcomponents/cheatsheet](https://www.creative-tim.com/twcomponents/cheatsheet)==

### 1. **Tailwind Configuration (**`**tailwind.config.js**`**)**

This is the heart of customizing Tailwind for your project.

- **Theme customization:**
    
    You can extend or override the default design system — colors, fonts, spacing, breakpoints, shadows, border-radius, and more.
    
    Example:
    
    ```JavaScript
    module.exports = {
      theme: {
        extend: {
          colors: {
            brandBlue: '\#1fb6ff',
            brandPink: '\#ff49db',
          },
          spacing: {
            '72': '18rem',
            '84': '21rem',
          },
        },
      },
    }
    ```
    
- **Variants:**
    
    Control which variants are generated, e.g., `hover:`, `focus:`, `active:`, `dark:`, etc.
    
- **Purge settings:**
    
    Tell Tailwind where to look for class names so it can remove unused CSS for production.
    

---

### 2. **Plugins**

Tailwind has an official plugin system that lets you:

- Add **custom utilities**, **components**, or **variants**.
- Integrate third-party plugins (e.g., forms, typography, aspect-ratio).
- Write your own plugin to generate specific classes or behaviors.

Example:

Add official typography plugin in `tailwind.config.js`:

```JavaScript
module.exports = {
  plugins: [
    require('@tailwindcss/typography'),
  ],
}
```

---

### 3. **Variants**

Variants are ways to apply styles conditionally:

- Responsive variants: `sm:`, `md:`, `lg:`, `xl:`
- State variants: `hover:`, `focus:`, `active:`, `disabled:`
- Dark mode variants: `dark:`

You can customize which variants Tailwind generates for different utilities in the config.

---

### 4. **Dark Mode**

Tailwind supports **dark mode** in two ways:

- **Class strategy:** Toggle a `.dark` class on the root element.
- **Media strategy:** Use the user's OS preference (`prefers-color-scheme`).

You enable it in config like:

```JavaScript
module.exports = {
  darkMode: 'class', // or 'media'
}
```

---

### 5. **JIT Mode (Just-In-Time Compiler)**

- Generates styles **on-demand** as you write your classes instead of generating all utilities upfront.
- Faster builds and smaller CSS size.
- Enabled by default in Tailwind v3+.

---

### 6. **Customizing Fonts, Colors, and More**

You can easily customize:

- Font families
- Font sizes
- Color palettes
- Spacing scale
- Border radius sizes
- Shadows

All via the `theme` object in the config.

---

### 7. **Using Tailwind with JavaScript Frameworks**

- Tailwind integrates very well with React, Vue, Angular, Next.js, etc.
- You can use tools like `@apply` directive in CSS for reusable styles.
- Tailwind can be combined with CSS-in-JS or component libraries.

---

### 8. **The** `**@apply**` **Directive**

You can create reusable CSS classes by applying Tailwind utilities inside your CSS:

```CSS
.btn {
  @apply bg-blue-500 text-white font-bold py-2 px-4 rounded;
}
```

---

### 9. **Purging Unused CSS**

To keep the final CSS file small, Tailwind removes any classes not used in your HTML or JS files during production builds.

You configure this in your `tailwind.config.js`:

```JavaScript
module.exports = {
  content: ['./src/**/*.{html,js,jsx,ts,tsx}'],
}
```
