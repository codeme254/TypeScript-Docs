# Top Types

In TypeScript, top types are types that can represent any value.

They can accept any value without causing a type error.

The two top types in TypeScript are:
- `any`: the most permissive types.
- `unknown`: a safer alternative to `any`.

## `any`
The `any` type allows you to assign any value to a variable and perform any operation on it without TypeScript 
complaining.

```TypeScript
let myVar: any = 55;
console.log(myVar); // 55

myVar = "Hello, World";
console.log(myVar); // Hello, World

myVar = [3, 12, 55];
console.log(myVar); // [3, 12, 55]

myVar = {}
console.log(myVar); // {}

console.log(myVar.toUpperCase()); // no error thrown
```

Avoid using the `any` type most of the time because it disables type checking, making TypeScript useless.

## `unknown`
The `unknown` type is like any, but it forces you to check the type before using it.

```TypeScript
let myVar: unknown = 55;
console.log(myVar); // 55

myVar = "Hello, World";
console.log(myVar); // Hello, World

myVar = [3, 12, 55];
console.log(myVar); // [3, 12, 55]

myVar = {}
console.log(myVar); // {}

console.log(myVar.toUpperCase()); // throws an error
```

`Unknown` type forces you to check a value before using it:

```TypeScript
let myVar: unknown = "Hello";
// console.log(myVar.toUpperCase()); // throws an error
if (typeof myVar === "string") {
  console.log(myVar.toUpperCase()); // works fine
}
```