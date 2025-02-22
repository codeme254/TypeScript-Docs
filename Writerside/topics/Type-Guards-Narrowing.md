# Type Guards/Narrowing

Type guards in TypeScript are a way to ensure that a variable is of a specific type within a certain scope.

They help in narrowing down the type of a variable, making your code safer and more predictable.

**Type guards** are expressions that check the type of a value at runtime.

TypeScript provides multiple ways to perform type guarding:
- `instanceof`
- `typeof`
- Type predicate (`is`)

## `instanceof` Type Guard
The `instanceof` operator is used to check if an object is an instance of a specific class.

```TypeScript
class Animal {
  makeSound() {
    console.log("Animal making sound");
  }
}

const dog: Animal = new Animal();
console.log(dog instanceof Animal); // true
```

## `typeof` Type Guard
The `typeof` operator checks the primitive type of a value.
```TypeScript
function processValue(value: string | number): void {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  } else {
    console.log(Math.sqrt(value));
  }
}

processValue(16);
processValue("Hello, world!!!");
```

## Type predicate (`is`)
A type predicate is a function that returns true when a value matches a specific type.

This is useful for custom type guards.

The general syntax is:
```TypeScript
function isType(value: any): value is Type
```

A basic example:
```TypeScript
function isString(value: any): value is string {
  return typeof value === "string";
}

console.log(isString("Hello, World!")); // true
console.log(isString(391)); // false
```

A more concrete example:
```TypeScript
type Fish = { swim: () => void };
type Bird = { fly: () => void };

function isFish(animal: Fish | Bird): animal is Fish {
  return (animal as Fish).swim !== undefined;
}

function move(animal: Fish | Bird) {
  if (isFish(animal)) {
    animal.swim();
  } else {
    animal.fly();
  }
}

const shark: Fish = { swim: () => console.log("Swimming...") };
const eagle: Bird = { fly: () => console.log("Flying...") };

move(shark); // "Swimming..."
move(eagle); // "Flying..."

```