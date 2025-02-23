# Generics

Generics allow you to define a placeholder type that can be specified when the construct(e.g. function, class e.t.c) 
is used, making the code more flexible and type-safe.

Consider the code below:

```TypeScript
class DataStore {
  private data: number[] = [];

  addItem(item: number): void {
    this.data.push(item);
  }

  getItem(idx: number): number | null {
    if (idx < 0 || idx >= this.data.length) return null;
    return this.data[idx];
  }

  getAllItems(): number[] {
    return this.data;
  }
}
```

The code above is an implementation for a DataStore class that only stores numbers.

What if we wanted to now store strings or even booleans? We would have to copy the entire class and maybe start 
changing the data types.

But this is not really what we would want to do, and it doesn't make sense when the only thing we want to 
change in our class is the type that we are using.

We need a way to variably be able to pass in a type and use a different type based on the instance of the class 
that we need.

This is where generics come in.

In TypeScript, generics are a way to create reusable components that can work with different data types.

**Generics allow you to define a placeholder type that can be specified when the component is used, making the 
code more flexible and type-safe.**

A generic is defined by placing a type parameter in angle brackets `<T>` after the function, class, or interface name.

T is a common placeholder name, but you can use any identifier.

```TypeScript
class DataStore<T> {
  private data: T[] = [];

  addItem(item: T): void {
    this.data.push(item);
  }

  getItem(idx: number): T | null {
    if (idx < 0 || idx >= this.data.length) return null;
    return this.data[idx];
  }

  getAllItems(): T[] {
    return this.data;
  }
}

const names = new DataStore<string>();
names.addItem("John");
names.addItem("June");
console.log(names.getAllItems());

interface User {
  name: string;
  age: number;
}

const users = new DataStore<User>();
users.addItem({ name: "john", age: 25 });
users.addItem({ name: "jane", age: 35 });
users.addItem({ name: "jack", age: 55 });
console.log(users.getAllItems());
```

## Generic Types
### Using generics in functions
A generic function uses a type parameter (`<T>`) to allow flexibility while maintaining type safety.
```TypeScript
function printItem<T>(item: T): T {
  return item;
}
console.log(printItem<string>("John"));
console.log(printItem<number>(25));

interface User {
  name: string;
  age: number;
}

console.log(printItem<User>({ name: "John", age: 33 }));
```
**Note: TypeScript can infer the type from the argument, so we don’t always need to specify it.**

```TypeScript
console.log(printItem("John"));
console.log(printItem(25));
console.log(printItem({ name: "John", age: 33 }));
```

### Using Generics in interfaces
We can also define interfaces with generics.

```TypeScript
interface Box<T> {
  value: T;
}

const numberBox: Box<number> = { value: 55 };
const stringBox: Box<string> = { value: "Hello" };
console.log(numberBox, stringBox);
```
- `Box<T>` is a generic interface.
- `T` allows it to store any type while ensuring consistency.

## Generic Constraints
By default, generics accept any type, but sometimes we want to restrict the allowed types.

### Constraining with `extends`
We can limit the generic type to a specific type or structure using `extends`.

```TypeScript
function processValue<T extends string | number>(value: T) {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  } else if (typeof value === "number") {
    console.log(value * 1000);
  }
}

processValue("john");
processValue(25);
processValue(true); // will not work
```

### Constraining to Specific Object Types
We can make sure that objects have specific properties using `extends` as shown:
```TypeScript
interface Id {
  id: number;
}

function printUserInfo<T extends Id>(user: T) {
  console.log(user);
}

printUserInfo({ id: 55, name: "John" });
printUserInfo({ id: 155, name: "Jack", age: 55, department: "Engineering" }); // works
// printUserInfo({name: "June"}); // will not work because the passed object has no id property
```