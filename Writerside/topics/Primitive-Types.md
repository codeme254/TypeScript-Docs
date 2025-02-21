# Primitive Types

Primitive types in TypeScript are the most basic types that represent simple values and are immutable.

They include **boolean**, **number**, **string**, **undefined**, and **null**.

## Numbers
Numeric values; could be positive numbers, negative numbers, 0, Infinity, -Infinity and floating point numbers.

Use the `number` keyword to define number data types in TypeScript:

```TypeScript
const myInteger: number = 5;
const negative: number = -48;
const myFloat: number = 56.835;
const zero: number = 0;
const infinity: number = Infinity;
const negativeInfinity: number = -Infinity;
```

## Strings
A string is a collection of characters enclosed within double, single quotes or backticks.

Use `string` keyword to define a string data type in TypeScript.

```TypeScript
const firstName: string = "John";
const lastName: string = "doe";
const emailAddress: string = `johdoe@gmail.com`;
const fullName: string = `${firstName} ${lastName}`;
```

## Booleans
Booleans can either be true or false.

Use `boolean` keyword to define a boolean data type in TypeScript.

```TypeScript
const isMale: boolean = true;
const isFemale: boolean = false;
```

## null
null is used when we want to explicitly define something that is empty or non-existent.

null variables automatically get `any` data type, which means they can hold values of any data type.

```TypeScript
let result = null;
result = true;
result = "john";
result = 25;
```

A simple fix for this would be to use the `null` data type as shown, and the variable will never accept any 
other data type:

```TypeScript
let result:null = null;
```

## undefined
undefined is used as a placeholder to mean that a variable has been declared but has not yet been assigned a 
value but will have a value soon.

Undefined has also its own keyword which is `undefined`;