# Bottom Types

In TypeScript, a bottom type is a type that represents a value that never exists.

The only bottom type in TypeScript is `never`, which is a type that represents values that never occur.

The never type is used in situations where a value can never be observed.

This usually happens in:
- Functions that never return (e.g., infinite loops and errors)
- Exhaustive switch-case handling
- Unreachable code.

We will talk more about the `never` type later.