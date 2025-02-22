# Combining Types

TypeScript provides several ways to combine and manipulate types, allowing for more flexibility and code reuse.

The key techniques include:
- Union Types
- Type aliases
- Intersection types
- The `keyof` operator

## Union (`|`)
Union types are used when a value can be more than a single type.

It means **"either one type or another."**

```TypeScript
let myVariable: string | number;

myVariable = "Hello, World!"; // valid
myVariable = 44; // valid
myVariable = false; // invalid
```

## Type Aliases (`type`)
A type alias gives a **custom name** to a type, making complex types easier to read and reuse.

Type aliases use the `type` keyword.

```TypeScript
type idNumber = string | number;

let userId: idNumber = 35552;
let anotherId: idNumber = "LkVH281";

console.log(userId, anotherId);
```

We can also use Type Alias with objects:

```TypeScript
type User = {
  firstName: string;
  lastName: string;
  age: number;
};

const john: User = {
  firstName: "John",
  lastName: "Doe",
  age: 34,
};

console.log(john);
```

## Intersection Types (`&`)
An intersection type combines multiple types into one, meaning the variable must satisfy all types.

Intersection types allow you to combine multiple types into one.

This means that the resulting type will have all the properties of the intersected types. 

You can create an intersection type using the `&` operator.

Let's say you have two interfaces, `Person` and `PersonDetails`, and you want to create a new type that includes 
properties from both:

```TypeScript
interface Person {
  firstName: string;
  lastName: string;
}

interface PersonDetails {
  location: string;
  email: string;
  phoneNumber: string;
}

type Employee = Person & PersonDetails;

const john: Employee = {
  firstName: "John",
  lastName: "Doe",
  location: "Fake ST",
  email: "John@gmail.com",
  phoneNumber: "+234023849453",
};

console.log(john);
```

## `keyof` Operator
`keyof` is a keyword in TypeScript that is used to extract the key type from an object type.

It allows you to extract the keys of an object type as a union of string or numeric literal types.

```TypeScript
interface Person {
  firstName: string;
  lastName: string;
  age: number;
}

type Keys = keyof Person;

let x: Keys = "firstName";
let y: Keys = "lastName";
let z: Keys = "age";

console.log(x, y, z);

// Type '"Hello, World"' is not assignable to type 'keyof Person'
let something: Keys = "Hello, World";

```