# TypeScript Setup

To install TypeScript, we need npm (Node Package Manager), which comes bundled with Node.js. If you haven't installed 
Node.js yet, you can download and install it from the [official Node.js website](https://nodejs.org/en/download).

You can verify whether you have Node.js installed by running the following command:

```Bash
node --version
```

If the command returns a version number, then you have Node.js installed, you can also verify that npm is 
available by running the following command in your terminal:

```Bash
npm --version
```

Similarly, if the command returns a version number, then you have npm installed.

If `npm` is installed, you can proceed to install TypeScript globally by running the following command:

```Bash
npm install -g typescript
```

After the installation, verify that TypeScript is installed by checking its version:

```Bash
tsc -v
```

If the command returns a version number, it means TypeScript is installed.

Now, you're ready to use TypeScript in your projects. 

To initialize a TypeScript project, navigate to your project directory and run:

```Bash
tsc --init
```

or

```Bash
npx tsc --init
```

This will generate a `tsconfig.json` file, which contains configuration options for your TypeScript project.

You can modify this file based on your project needs (more about this later).

## Your first TypeScript code
With the above setup complete, let's now write our first TypeScript code.

Inside your project directory, create a file `hello.ts` with the following code:

```TypeScript
let age: number = 55;
console.log(age);
```

To execute the code above, we need to convert it to JavaScript code first and then execute the generated JavaScript 
code.

To do this, navigate to where the file `hello.ts` lives and run the following command:

```Bash
tsc hello.ts
```

This will generate `hello.js` with the following code:

```JavaScript
var age = 55;
console.log(age);
```

We can then execute this JavaScript with node or view its output in the browser.