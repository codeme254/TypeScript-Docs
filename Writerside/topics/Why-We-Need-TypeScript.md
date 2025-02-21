# Why We Need TypeScript

Every programming language has its own problems and surprises; JavaScript has many of these, which can become 
problematic, especially in large-scale applications:

**Examples**:  
**JavaScript allows accessing properties which aren't present in an object**:
```JavaScript
const rectangle = { width: 300, height: 400 };
const area = rectangle.width * rectangle.something;
console.log(area);
```
Normally, if we try to access a property that doesn't exist in an object, most programming languages would throw an
error.

The code below is also legal and will work in JavaScript:
```JavaScript
console.log(4 / []);
```
[More examples](https://github.com/denysdovhan/wtfjs)

Here are the reasons as to why we need TypeScript:

## Type Safety (Fewer Runtime Errors)
JavaScript is dynamically typed, meaning type-related errors often appear at runtime. TypeScript catches 
these errors at compile time, reducing bugs.

For example, the function below expects numbers but nothing will prevent passing a string:
```JavaScript
function add(a, b) {
  return a + b;
}
console.log(add(5, "10")); // Output: "510" (Bug: Should be 15)
```

## Better Code Readability and Maintainability
In large codebases, JavaScript's dynamic nature makes it hard to understand what a function expects or returns.

For example, in the JavaScript function below, it is not clear whether the function is adding numbers, or strings or
even arrays; we just assume that it is adding two numbers.

```JavaScript
function add(a, b) {
  return a + b;
}
```

## Enhanced IDE support and AutoCompletion
With TypeScript, editors like VS Code provide:
- Autocomplete and intelliSense
- Error checking as you type
- Quick refactoring and navigation 🔍
This boosts developer productivity compared to JavaScript.

## Scalability for Large Applications
JavaScript works well for small projects, but as applications grow, it becomes harder to manage.
- No type enforcement leads to hidden bugs.
- Developers struggle to understand data structures.
TypeScript enforces structure in the code, making collaboration and scaling easier.

## Easier Refactoring Debugging
Renaming variables, moving functions, and restructuring code is safer in TypeScript because the compiler 
ensures consistency.
Example:
- In JavaScript, renaming a function might break parts of your app.
- In TypeScript, the compiler warns you about all affected places.

## Popularity and Industry Adoption
Many major companies (Google, Microsoft, Airbnb, etc.) use TypeScript for large projects.
- Used in frameworks like Angular, NestJS, Next.js, etc.
- Adopted in backend (Node.js) & frontend (React, Vue, Angular).