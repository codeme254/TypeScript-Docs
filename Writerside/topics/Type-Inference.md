# Type Inference

Type inference in TypeScript is the ability of the compiler to automatically determine the type of a variable based 
on its assigned value, without explicitly specifying the type.

```TypeScript
let message = "Hello, TypeScript"; // Inferred as string
let count = 10; // Inferred as number
```

Since `message` is assigned a string, TypeScript infers its type as string, preventing accidental assignment of 
other types later.

```TypeScript
let message = "Hello, TypeScript"; // Inferred as string
let count = 10; // Inferred as number
message = 200; // Error: Type number is not assignable to type 'string'
count = "Hello, world"; // Error: Type 'string' is not assignable to type 'number'
```