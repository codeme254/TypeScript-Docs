# Classes

Classes in TypeScript provide a way to create reusable blueprints for objects, following object-oriented 
programming (OOP) principles.

## Declaring a Class in TypeScript
A class is defined using the class keyword. It can have properties and methods.

```TypeScript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const person1 = new Person("John", 25);
person1.greet();
```
- `name` and `age` are properties.
- The `constructor` initializes the properties when creating an instance.
- `greet` is a method (a function inside a class/an object).

## Access Modifiers
In object-oriented programming, access modifiers are keywords that set the accessibility (visibility) of classes, 
methods, and properties.

They control whether certain elements of a class can be accessed from outside the class or from within other classes, 
enforcing encapsulation and protecting data integrity.

JavaScript traditionally doesn't have access modifiers like other languages.

TypeScript, however, supports access modifiers.

The three access modifiers are:
- **public**: default, accessible anywhere.
- **private**: accessible only within the class
- **protected**: accessible within the class and subclasses.

### private
When we mark a property or method as private, it can only be accessed within the class where it is defined.

This restricts direct access from outside the class (including subclasses), promoting encapsulation and safeguarding 
the data from unintended modifications.

```TypeScript
class Person {
  private name: string;
  private age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }

  private sayGoodbye(): void {
    console.log(`Goodbye`);
  }
}

const person1 = new Person("John", 25);
person1.greet();

console.log(person1.name); // will not work
person1.sayGoodbye(); // will not work as well
```

### protected
A modifier that allows a property or method to be accessed within its own class and subclasses, but not from outside.

When you mark a property or a method as protected, it can only be accessed within the class or within the classes 
that inherit from it but not outside.

```TypeScript
class Person {
  protected name: string;
  protected age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }
}

class Student extends Person {
  sayGoodbye() {
    console.log(`Goodbye, this has been ${this.name}`);
  }
}

const john = new Student("John", 25);
john.sayGoodbye(); // works
console.log(john.name); 
// Property 'name' is protected and only accessible within class 'Person' and its subclasses
```

### Public
Public is the default access modifier, which means the property can be accessed from anywhere.

```TypeScript
class Person {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const john = new Person("John");
john.greet();
```

## Abstract Classes
An abstract class refers to a restricted class that cannot be used to create objects and designed to be 
specifically used as a base class.

An abstract class serves as a base class that cannot be instantiated but can define common methods for subclasses.

You cannot create an instance of an abstract class, you can extend it, override functionality, but you can't 
instantiate it.

Abstract classes can be used as 'blueprint for other classes.'

An abstract class is defined using the `abstract` keyword.

Subclasses must implement any methods inside an abstract class marked with the `abstract` keyword.

```TypeScript
abstract class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  // The method below must be implemented by subclasses
  abstract makeSound(): void;

  move(): void {
    console.log(`Animal moving`);
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("Bark!");
  }
}

const dog = new Dog("Jimmy");
console.log(dog.name);
dog.makeSound();
dog.move();
```

## Classes and Interfaces
Classes can also implement interfaces.

A class can implement an interface, enforcing that it follows a specific structure.

Interfaces don't implement any functionality or behavior, this is their fundamental difference from abstract classes, 
abstract classes can implement some methods.

```TypeScript
interface Animal {
  name: string;
  age: number;
  makeSound: () => void;
  move: (numLegs: number) => void;
}

class Dog implements Animal {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  makeSound(): void {
    console.log("Bark!");
  }

  move(numLegs: number): void {
    console.log(`Dog moving with ${numLegs} legs`);
  }
}

const dog = new Dog("Jimmy", 5);
dog.makeSound();
dog.move(4);
```