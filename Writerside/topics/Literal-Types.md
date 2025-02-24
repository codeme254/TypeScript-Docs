# Literal Types

Literal types allow a variable to have a specific string, number, or boolean value instead of general types.

```TypeScript
type Status = "success" | "error" | "loading";

let state: Status = "success";
state = "loading";
state = "error";
// state = "failure"; // will not work
```

## Template literal types
These allow us to construct new types using template literals, similar to JavaScript string templates.

```TypeScript
type Shade = "dark" | "light";
type Color = "red" | "green";

type ColorShade = `${Shade}-${Color}`;
// "dark-red" | "dark-blue" | "light-red" | "light-blue"

let color: ColorShade = "light-green";
console.log(color);
```