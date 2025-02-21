# Dynamic vs. Static Typing

All major programming languages that we work with are either **dynamically typed** or **statically typed**.

**Dynamically typed** means that the type of variables can change at runtime.

In dynamically typed languages, data types are determined at runtime, meaning you don’t need to explicitly 
declare variable types.

Examples of dynamically typed languages include: JavaScript, Perl, PHP, Python e.t.c.

Example in JavaScript:
```JavaScript
let x = 5; // x is a number
x = "Hello"; // x is now a string (no error)
console.log(x); // Output: Hello
```

In the example above, the variable `x` starts as a number but is later assigned a string without any issue.

**Statically typed** means that the type of variables cannot change once declared.

In **statically typed** languages, data types are checked at compile time, meaning you must explicitly declare or 
infer variable types.

Examples of statically typed languages include: TypeScript, Java, C++, C#, Swift e.t.c.

Example in TypeScript:
```TypeScript
let x: number = 5; // x is explicitly declared as a number
x = "Hello"; // Error: Type 'string' is not assignable to type 'number'
```