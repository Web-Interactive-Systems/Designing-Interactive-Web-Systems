---
type: NoteCard
tags: []
---

# JavaScript Modules
> A system that enables compartmentalization and organizing of code into separate, reusable pieces.

In JavaScript, modules are implemented using the import/export syntax.

## Export

To make a variable, function, or class available for use in another file, it must be exported. This is done using the **`export`** keyword.

```js
// file: myModule1.js

export const myVariable = "hello";
export function myFunction() { /* ... */ }
export class MyClass { /* ... */ }

// these functions can be imported in other files
```

## Default export

A module can have a single default export, which is the main thing that it exports. The default export can be any value or function.

```js
// myModule2.js

// see the keyword `default`,
export default function() { /* ... */ }
```

## Import

To use a variable, function, or class from another file, it must be imported. This is done using the import keyword.

```js
// anotherModule1.js

import { myVariable, myFunction, MyClass } from "./myModule1.js";

// importing the default module
```

## Importing the default export

To import the default export from a module, use the import statement without curly braces.

```js
// anotherModule2.js
import myFunction from "./myModule2.js";
```

## Renaming imports/exports

It's possible to give imported or exported values a different name using the as keyword.

```js
// anotherModule3.js
import { myVariable as anotherName } from "./myModule1.js";

// anotherName is the new name of myVariable within this file
```

## Dynamic imports

It's possible to load a module dynamically at runtime using the import() function. This returns a Promise that resolves to the module.

```js
import("./myModule.js").then(module => {
  // Do something with the module
});


// Or
await import("./myModule.js")
```

## Circular dependencies

If two or more modules depend on each other, it's called a circular dependency. This can cause problems and should be avoided.

```js
// module1.js
import { func2 } from "./module2.js";
export function func1() { /* ... */ }

// module2.js
import { func1 } from "./module1.js";
export function func2() { /* ... */ }
```