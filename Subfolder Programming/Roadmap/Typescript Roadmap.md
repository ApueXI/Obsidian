# 🧭 **TypeScript Roadmap (Core Language Only)**

---

## 🔰 **1. Introduction to TypeScript**

- What TypeScript is (superset of JavaScript)
    
- Why static typing matters
    
- Type checking vs. runtime behavior
    
- Installing the compiler: `npm install -g typescript`
    
- Compiling: `tsc file.ts`
    
- Config file: `tsconfig.json` basics
    

---

## 📝 **2. Basic Types**

- `string`, `number`, `boolean`
    
- `null`, `undefined`, `unknown`, `any`
    
- Arrays (`number[]`, `Array<string>`)
    
- Tuples (`[number, string]`)
    
- Enums (`enum Direction { ... }`)
    
- Literal types (`"left" | "right"`)
    

---

## 🧱 **3. Type System (Core Concepts)**

- Type inference
    
- Widening vs. narrowing
    
- Union types (`number | string`)
    
- Intersection types (`A & B`)
    
- Type aliases (`type Age = number;`)
    
- Interfaces (object shapes)
    
- Extending interfaces
    
- Difference between `type` and `interface`
    

---

## 🧩 **4. Functions**

- Function typing:
    
    `function add(a: number, b: number): number {}`
    
- Optional parameters (`b?: number`)
    
- Default parameters (`b: number = 1`)
    
- Rest parameters (`...args: number[]`)
    
- Function types and signatures
    
- Overloads
    
- Callbacks
    
- `void` vs `never`
    

---

## 🏗️ **5. Object Types**

- Inline object types
    
- Readonly properties (`readonly name: string`)
    
- Index signatures (`[key: string]: number`)
    
- Type narrowing with `in`, `typeof`, and `instanceof`
    
- Structural typing (important TS concept)
    

---

## 🏛️ **6. Classes (Pure TypeScript OOP)**

- `class`, `constructor`, methods
    
- `public`, `private`, `protected`
    
- `readonly` class fields
    
- Static properties/methods
    
- Inheritance (`extends`)
    
- Abstract classes
    
- Getters and setters
    
- Implementing interfaces
    

---

## 🔗 **7. Modules**

- Import/export syntax
    
- Named exports
    
- Default exports
    
- Re-exporting
    
- Type-only imports (`import type { X } from ...`)
    

---

## 🧠 **8. Generics**

- Generic functions
    
- Generic interfaces
    
- Generic classes
    
- Constraints `<T extends SomeType>`
    
- Built-in generics (`Promise<T>`, `Map<K, V>`, `Set<T>`)
    

---

## 🎯 **9. Advanced Types**

- Mapped types
    
- Conditional types (`T extends U ? X : Y`)
    
- Template literal types
    
- Keyof operator (`keyof T`)
    
- Indexed access types (`T[K]`)
    
- Optional & required modifiers (`Partial`, `Required`, `Readonly`)
    
- Record type (`Record<Keys, Type>`)
    
- Discriminated unions
    
- Exhaustiveness checking
    

---

## 🧩 **10. Utility Types (Core)**

- `Partial<T>`
    
- `Required<T>`
    
- `Readonly<T>`
    
- `Pick<T, K>`
    
- `Omit<T, K>`
    
- `Record<K, T>`
    
- `ReturnType<T>`
    
- `InstanceType<T>`
    
- `Extract` / `Exclude`
    
- `Awaited<T>`
    

---

## 🧪 **11. Type Narrowing (VERY important)**

- `typeof` narrowing
    
- `instanceof` narrowing
    
- `in` operator narrowing
    
- Control-flow-based narrowing
    
- Type predicates:
    ```TS
    function isString(x: unknown): x is string {}
    ```
    

---

## ⚙️ **12. Compiler Configuration (tsconfig)**

- `strict` mode
    
- `target` (ES5, ES6, ES2020, etc.)
    
- `module` (CommonJS, ESNext, etc.)
    
- Module resolution
    
- Source maps
    
- `noImplicitAny`
    
- `noFallthroughCasesInSwitch`
    
- `skipLibCheck`
    
- `resolveJsonModule`
    

---

## 🔒 **13. Type Safety Techniques**

- Avoiding `any`
    
- Using `unknown` properly
    
- Branding types (type-safe IDs)
    
- Exhaustive `switch` with `never`
    
- Using type guards
    

---

## 🧱 **14. Core TypeScript Philosophy**

- Duck typing / structural typing
    
- Everything is about object _shape_, not classes
    
- Type system is erased at runtime
    
- Types exist only at compile time
    

---

## 🛠️ **15. Extra Advanced Topics**

- Declaration merging
    
- Ambient declarations (`declare`)
    
- Writing `.d.ts` files
    
- Ambient modules
    
- Namespaces (legacy, but part of TS)
    
- Augmenting global types
    
- Implementing interfaces with functions
    
- Typing complex callback chains
    
- Branded/opaque types
    

---

# 🎓 **What You Can Do with Pure TypeScript**

(Without frameworks or imports)

✔ Learn full static typing  
✔ Create CLI apps (compiled to JS)  
✔ Build your own type-safe libraries  
✔ Implement full OOP with strong typing  
✔ Build reusable utilities with generics  
✔ Catch runtime bugs during compile-time  
✔ Build safe APIs, validators, and data models  
✔ Learn advanced type-level programming