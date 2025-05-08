# L2A1

# TypeScript Interview Questions – Explained in Simple Terms

TypeScript is a powerful superset of JavaScript that brings static typing and improved developer experience. In this blog post, we’ll break down two frequently asked TypeScript interview questions with clear examples and comparisons:

## Topics Covered:

1. What are the differences between `interface` and `type` in TypeScript?
2. What is the difference between `any`, `unknown`, and `never`?

---

## 1. Differences Between `interface` and `type` in TypeScript

Both `interface` and `type` are used to define the structure of objects, but they have some key differences in how they work and where they are best used.

### Interface:

- Specifically designed to define the shape of objects.
- Supports extension using `extends`.
- Can be declared multiple times (declaration merging).

### Type:

- Can define not only object structures but also unions, intersections, tuples, etc.
- Cannot be re-declared once defined.
- More flexible in complex type compositions.

### Example:

```ts
// Using interface
interface User {
  name: string;
  age: number;
}

// Using type
type Admin = {
  name: string;
  role: string;
};
```

## 2. What is the difference between `any`, `unknown`, and `never`

1. any

   - Definition: any allows a variable to hold any type of value, and disables all type checking.

   - Use Case: When you don’t know or don’t care about the type of a variable.
   - Risk: It turns off TypeScript's type safety, so it should be avoided if possible.

```ts
let anything: any = "Hello";
anything = 42;
anything = true;
anything.toUpperCase();
```

2. unknown

   - Definition: unknown also allows any type, but it’s type-safe. You must narrow or check the type before using it.

   - Use Case: When you're accepting any value, but want to enforce type-checking before using it.

   - Safe Alternative: Use unknown instead of any when you're unsure of the type.

```ts
let value: unknown = "Hello";
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

3. never
   - Definition: never represents a value that never occurs. Typically used in:
     1. Functions that always throw errors
     2. Functions with infinite loops
     3. Exhaustive checks (e.g., switch statements)
   - Use Case: To indicate code paths that should not happen.

function throwError(message: string): never {
throw new Error(message);
}

```ts
function process(value: string | number) {
  if (typeof value === "string") {
    console.log("String:", value);
  } else if (typeof value === "number") {
    console.log("Number:", value);
  } else {
    // This block should never run
    const neverValue: never = value;
  }
}
```
