# Object Types

In TypeScript, object types define the shape of complex values.

The most common object types include:
1. **Interface** - Defines a shape for an object structure.
2. **Class** - Defines blueprints for creating objects.
3. **Enum** - Represents a set of named constant values.
4. **Array**—Represents a collection of elements that are of the same type.
5. **Tuple** - Represents an ordered list of elements with fixed types and lengths.

## Interface
An interface defines the structure of an object.

It’s used for type checking objects and enforcing consistency.

```TypeScript
interface User {
  firstName: string;
  lastName: string;
  age: number;
  isAdmin: boolean;
}

const john: User = {
  firstName: "John",
  lastName: "Doe",
  age: 25,
  isAdmin: false,
};
```

### Optional properties for interface
We can use `?` to show optional properties.

In the example below, `isAdmin` property is optional:

```TypeScript
interface User {
  firstName: string;
  lastName: string;
  age: number;
  isAdmin?: boolean;
}

const john: User = {
  firstName: "John",
  lastName: "Doe",
  age: 25,
};

console.log(john);
```

### Readonly properties for interfaces
Use the `readonly` keyword for properties that should not be modified.

```TypeScript
interface User {
  firstName: string;
  lastName: string;
  age: number;
  readonly isAdmin: boolean;
}

const john: User = {
  firstName: "John",
  lastName: "Doe",
  age: 25,
  isAdmin: false
};

// john.isAdmin = true;
// cannot assign to 'isAdmin' because it is a read-only property
console.log(john);
```

### Extending interfaces
Extending interfaces means creating a new interface that inherits properties from an existing one, allowing for reuse.

Use the `extends` keyword.

```TypeScript
interface User {
  firstName: string;
  lastName: string;
  age: number;
  readonly isAdmin: boolean;
}

interface Employee extends User {
  employeeId: string;
  department: string;
  role: string;
}

const jane: Employee = {
  firstName: "Jane",
  lastName: "Doe",
  age: 35,
  isAdmin: false,
  employeeId: "EMP0035LKV",
  department: "Engineering",
  role: "Developer",
};

console.log(jane);
```

## Class
A class is a blueprint for creating objects with properties and methods.

When creating a class in TypeScript, we start by defining the properties then initialize those properties in the
constructor function.

```TypeScript
class User {
  firstName: string;
  lastName: string;
  age: number;

  constructor(firstName: string, lastName: string, age: number) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
  }

  printInformation() {
    console.log(`My name is ${this.firstName} ${this.lastName}. I am ${this.age} years old`,);
  }
}

const john: User = new User("John", "Doe", 35);
john.printInformation();
```

We will learn more about classes in TypeScript later.

## Enum
An enum is a special type that defines a set of named constants.

Enums can help prevent invalid values and ensure consistency.

There are two types of enums:
- Numeric enums
- String enums

### Numeric Enums
Numeric enums in TypeScript assign numerical values to their members, starting from 0 with subsequent members 
auto-incrementing.

```TypeScript
enum PizzaSize {
  Small, // 0
  Medium, // 1
  Large, // 2
  ExtraLarge, // 3
}

console.log(PizzaSize.Small); // 0
console.log(PizzaSize.ExtraLarge); // 3

let orderedPizzaSize: PizzaSize = 0;

if (orderedPizzaSize === PizzaSize.Small) {
  console.log(`Pay $5`);
}
```

Numeric enums start from 0 and the rest of the elements automatically increment by 1, we can change the starting point
as shown:

```TypeScript
enum PizzaSize {
  Small = 100,
  Medium,
  Large,
  ExtraLarge,
}

console.log(PizzaSize.Small); // 100
console.log(PizzaSize.Medium); // 101
console.log(PizzaSize.Large); // 102
console.log(PizzaSize.ExtraLarge); // 103

```

We can also set completely custom integer values as shown:

```TypeScript
enum PizzaSize {
  Small = 100,
  Medium = 200,
  Large = 300,
  ExtraLarge = 400,
}

console.log(PizzaSize.Small); // 100
console.log(PizzaSize.Medium); // 200
console.log(PizzaSize.Large); // 300
console.log(PizzaSize.ExtraLarge); // 400
```

### String Enums
String enums in TypeScript assign string values to their members explicitly, ensuring each member holds a unique 
string value.

```TypeScript
enum PizzaSize {
  Small = "Small",
  Medium = "Medium",
  Large = "Large",
  ExtraLarge = "ExtraLarge",
}

console.log(PizzaSize.Small); // Small
console.log(PizzaSize.Medium); // Medium
console.log(PizzaSize.Large); // Large
console.log(PizzaSize.ExtraLarge); // ExtraLarge
```

## Array
An array is a collection of elements that have the same type.

```TypeScript
let luckyNumbers: number[] = [33, 28, 23, 5, 96, 68];
console.log(luckyNumbers);
```

If you want your array to hold items of various data types, you can specify these data types using the **union type**
(more about union type later).

```TypeScript
let luckyNumbers: (number | string | boolean)[] = ["cat", 5, true, 96];
console.log(luckyNumbers);
```

## Tuple
A tuple is a special kind of array with fixed types and a fixed number of elements.

**Example: defining an array:**
```TypeScript
let userInfo: [string, number] = ["John", 25];
console.log(userInfo);
```

### Named Tuples
Named tuples in TypeScript allow you to give labels to tuple elements, improving readability and maintainability.

Compare:
```TypeScript
let border: [string, string, string] = ["3px", "solid", "red"];
console.log(border);
```

With:
```TypeScript
let border: [width: string, style: string, color: string];
border = ["3px", "solid", "red"];
console.log(border);
```

### Tuples with optional elements
To specify that an element of a tuple is optional, use `?`.

```TypeScript
let border: [string, string, string?];
border = ["3px", "solid"];
console.log(border);
```

For named tuples:
```TypeScript
let border: [width: string, style: string, color?: string];
border = ["3px", "solid", "red"];
console.log(border);
```
