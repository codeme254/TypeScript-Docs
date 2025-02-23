# Utility Types

Utility types are built-in types that enable you to transform and manipulate existing types in various ways.

## Partial (`Partial<T>`)
Partial utility type takes an exiting type and makes all its properties optional.

```TypeScript
interface User {
  name: string;
  age: number;
  location: string;
}

const alice: Partial<User> = {};
console.log(alice); // works

const john: Partial<User> = {
  name: "John",
};

console.log(john); // works
```

## Pick (`Pick<T, K>`)
Creates a new type by selecting a subset of properties `K` from type `T`.

Useful for extracting specific properties from a type.

```TypeScript
interface User {
  name: string;
  emailAddress: string;
  age: number;
  location: string;
}

type Student = Pick<User, "name" | "emailAddress" | "age">;

const john: Student = {
  name: "John Doe",
  emailAddress: "john@gmail.com",
  age: 24,
};

console.log(john);
```

We extract `name`, `emailAddress` and `age` from type `User` to make another type `Student`.

## Omit (`Omit<T, K>`)
Creates a new type by omitting specific properties `K` from type `T`.

Helpful when you want most properties from an existing type except a few.

```TypeScript
interface User {
  name: string;
  emailAddress: string;
  age: number;
  location: string;
}

type Student = Omit<User, "location">;

const john: Student = {
  name: "John Doe",
  emailAddress: "john@gmail.com",
  age: 24,
};

console.log(john);
```

## Readonly (`Readonly<T>`)
The `ReadOnly<T>` utility makes all properties **immutable**.

This means that these properties cannot be reassigned once created.

```TypeScript
interface User {
  name: string;
  emailAddress: string;
  age: number;
  location: string;
}

const john: Readonly<User> = {
  name: "John Doe",
  emailAddress: "john@gmail.com",
  age: 55,
  location: "Fake ST",
};

john.age = 55; 
// Error: Cannot assign to 'age' because it is a read-only property
```

## Record (`Record<K, T>)
Constructs an object type with keys `K` and values of type `T.

It is used to specify the type for keys and values.

```TypeScript
type Role = "admin" | "user" | "guest";
// Ensures that only admin, user, and guest keys exist
// and their values are an array of strings
type Permission = Record<Role, string[]>;

// now, any object created with type 'Permission'
// should have keys being either admin, user or guest

const appPermissions: Permission = {
  admin: ["Read", "Write", "Delete"],
  user: ["Read", "Write"],
  guest: ["Read"],
};

console.log(appPermissions);
```

## Exclude (`Exclude<T, U>`)
The `Exclude<T, U>` utility removes specific types from a union.

It removes type(s) `U` from union `T`

```TypeScript
type UserType = "admin" | "user" | "guest" | "child" | "other";
type AllowedTypes = Exclude<UserType, "child" | "other">;
// removes "child", "other"
```

## Extract (`Extract(T, U>`))
The `Extract<T, U>` utility keeps only the types that match.

```TypeScript
type UserType = "admin" | "user" | "guest" | "child" | "other";
type AllowedTypes = Extract<UserType, "admin" | "user" | "guest">;
// removes "child", "other"
```

## NonNullable (`NonNullable<T>`)
The `NonNullable<T>` utility removes `null` and `undefined` from a type.

```TypeScript
type UserEmail = string | null | undefined;
type ValidEmail = NonNullable<UserEmail>;

const johnEmail: ValidEmail = "john@gmail.com";
```