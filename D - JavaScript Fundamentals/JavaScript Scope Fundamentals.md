---
type: NoteCard
tags: []
---

# JavaScript Scope Fundamentals
Scope is an import concept of JS programming language, a concept that can be difficult to master. JS runtime uses scopes to determine which variables and functions are **:u[accessible]** and **:u[visible]** inside different code blocks of a JS file or a JS module.

::::cal
Every time we declare a variable or a function in JS its **visibility** and **accessibility** is limited depending on its scope.

::::

## Code blocks

Scope is related to `code blocks`. Code blocks are portions of code inside `{ … CODE … }`. Another special type of code block is the whole file or the module defined in a JS file.

Here are some examples:

```js
// --------- 
// file.js
// ---------

// a special type of code block
// is the whole file
// -> here is known as global scope 

{
// a code block
}

if (condition) {
// a code block
}

for (const element of items) {
// a code block
}

function sum(a, b) {
// a code block
}

// -> here is part of the global scope, because it is inside the file (not inside a code block)
```

## Block Scope

When we define variables in JS, they are defined inside specific scopes. You might have asked: How JS (runetime) distinguishes between two variables with the same name? How JS distinguishes between variables inside and outside functions and other blocks of code, such as switch, if conditions, loops, etc.

JS runetime **parse the code** to determine the scope of each variable.

## Global scope

Variables or functions defined ***outsides*** blocks are called **global**. They have a global scope and called global variable.

Global variables are **:u[visible]** to all other code blocks inside a JS file.

```js
// --------- 
// file.js
// ---------

// items is a global variable
let items = ['item 1', 'item 2'];

// doSomething is a global variable
const doSomething = function () {
  // code
}

// doAntherthing is a global function
function doAntherthing() {
  // another code
}
```

::::cal
A general recommendation is to avoid using global variables as much as possible. The reason is that they can easily lead to errors.

::::

## Local scope

In contrast to global scope, local scope relate to variables or functions declared inside code blocks.

```js
// --------- 
// file.js
// ---------

// someFunction is a global function
function someFunction() {
  // inside the body of the function if a local scope for this function

  // items is a local variable
  const items = ['item 1', 'item 2'].join(', ');

  // do something with items
  // ...
}

// items is not visible nor accessible outside someFunction

console.log('items is : ', items)

// What's the ouput ?
```

They are visible and accessible inside their local scope but not outside it. Therefore,  it is not possible to access or modify any local variable from the global scope or another local scope.

## Nested local scopes

We already seen a specific type of nested scopes. That is inside, a JS file or a module, all variables or functions are declared inside the global scope. The local scopes of variables or functions are nested inside the global scope. The rule is that the variables or functions defined inside outer scopes (parent) are visible inside inner scopes.

Similarly, we can create local scopes inside other local scopes. For example, we can declare a function inside another function. The variables or functions of the parent are visible and accessible inside the nested function.

```js
// --------- 
// file.js
// ---------

function someA() {
  //  local scope of someA

  // title is a local variable of someA
  let title = 'some interesting title';

  // someB is a local function of someA
  function someB() {
    //  local scope of someB

   // text is a local variable of someA
    let text = 'some interesting text';
  }
}
```

## Lexical scope

Inner functions have access to the variables we declare in the outer scopes. This aspect is called the lexical scope: the ability to access variables and functions from parents scopes.

Lexical scope works only from the top to bottom.

```js
// --------- 
// file.js
// ---------

 // ** text ** and ** title ** are NOT visible here

function someA() {
  //  local scope of someA

  // title is a local variable of someA
  let title = 'some interesting title';

  // ** text ** is NOT visible here

  // someB is a local function of someA
  function someB() {
    //  local scope of someB

   // ** title ** is visible here

   // text is a local variable of someA
    let text = 'some interesting text';
  }
}

 // ** text ** and ** title ** are NOT visible here
```

## Scope using let, const, and var

What we described about code blocks and their scopes is true when using `let` and `const` keywords. Variables defined using `let` and `const` are called block-scoped. Their visibility spens the block and nested blocks in which they are defined.

However, JS has another keyword called `var`. In modern JS `var` is banned, meaning, it is still exists in JS but it is stongly recommended to NOT use it and instead use `let` and `const`.

Variables declared using `var` are available throughout the file, module, block, or function in which they are declared.

Because `let` is block-scoped, it is not possible to redeclare a variable declared with `let` in the same scope. In addition, it is not possible to access a variable declared with `let` before its declaration statement. These constrains can prevent errors in the code.

```js
// x is accessible here but undefined
console.log(x);

var x = 5;

console.log(x);

// outputs:
 
// undefined
// 5
```

```js
// x is NOT accessible here
console.log(x);

let x = 5;

console.log(x);

// ReferenceError: Cannot access 'x' before initialization
```

```js
var a = 3;

console.log(a);

var a = 2:

a = 4;

console.log(a);

// outputs:
 
// 3
// 4
```

```js
let a = 3;

console.log(a);

let a = 2:

console.log(a);

// TypeError: Cannot redeclare block-scoped variable 
```

## Scope and hoisting

Hoisting refers to JavaScript's default behavior of **moving declarations to the top** (of blocks, functions, and modules). This feature is only for declarations (not initializations).

Becaus of this feature, we can access (use) variables declared using `var` before their declaration.

```js

// assign 5 to x
x = 5; 

console.log(x)

// declare x, this will be hoisted (moved to the top)
var x;

// outputs:
 
// 5

/// same if we replace var with let
```

```js
console.log(y)

// declare y, this will NOT be hoisted (moved to the top) because it is an initialization not declaration
var y = 7;

// outputs:
 
// undefined

/// same if we replace var with let
```

Below is a bit complex examples.

```js
var x = "X Outside";

function todo() {
  console.log("x : ", x);

  var x = "X Inside"; // save for let
}

todo();

// Outputs

// x :  undefined
```

::::cal
Here is a rough outline of how JS “compiler” will parse this code to determine the scropes:

*   First it will see `x` as global variable
*   Then, inside `todo` function will find a local variable with same name `x`
*   The local variable will override the global one for the scope of the `todo` function
*   Then, the local variable `x` is defined using an **initialization**, **it will not be hoited** (moved the top of the todo block)
*   When, running `console.log("x : ", x);` the x is :u[visible] but :u[undefined]

::::

```js

var a = 'value of a'; 

function todoB() {

   if ( false ) {
    var a = 'new value of a';
  }

  console.log( a );
}


todoB(); 

// outputs:

// undefined
```