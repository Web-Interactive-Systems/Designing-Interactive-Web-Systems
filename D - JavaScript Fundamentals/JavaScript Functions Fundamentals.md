---
type: NoteCard
tags: []
---

# JavaScript Functions Fundamentals
Functions are one of the most important building blocks of JavaScript. And there are varying ways of creating and working with functions in JS.

## Functions

A function is a block of code that performs a task, e.g., calculates a value. A function can take inputs (arguments) and return a value. A function is handled as a value, the same as an integer \`3\` or an array \`[1, 1, 4]\`. A function can return another function. A function can another function as input.

```js
function sayHello(name) {
  console.log("Hello, " + name + "!");

  return 'done';
}
```

## Procedures

Functions without a return.

```js
function showAlert(message) {
  alert("Alert, " + message + "!");
}
```

## **Function Declarations**

Function declations are a way to define a named function with the **`function`** keyword, which can be called later in the code. See below for other ways to define functions without the keyword **`function`.**

```js
function sayHello(name) {
  console.log("Hello, " + name + "!");
};

// use sayHello to call the function sayHello(...)
```

::::cal
**Notice that we use the keyword `function` and the name of the function `sayHello`.**

::::

## **Function Expressions**

Function expressions are a way to define an anonymous function as an expression, which can be assigned to a variable and passed around like any other value.

```js
// sayHello is a variable function
const sayHello = function(name) {
  console.log("Hello, " + name + "!");
};

// use sayHello to call the function sayHello(...)
```

::::cal
**Notice here that `sayHello` is the name of a :u[variable] and the function is created without a name — we call it an anonymous function.**

::::

## **Global Function Scope**

Functions declared in the global scope are accessible throughout the code. [See Function Hoisting below]

```js
// more code
// we can call sayHello(...) here

function sayHello(name) {
  console.log("Hello, " + name + "!");
};

// more code
// we can call sayHello(...) here as well
```

## Local Function Scope

Functions declared within other functions have access to their parent's variables, but their variables are not accessible outside of the function.

```js
function outerFunction() {
  const outerVariable = "I'm outer!";
  
  function innerFunction() {
    const innerVariable = "I'm inner!";
    console.log(outerVariable);
    console.log(innerVariable);
  }
  
  innerFunction();
}

outerFunction(); // Output: ??
```

## Closures

A function that returns another function, which can access the parent function's variables even after the parent function has finished executing.

```js
function add5(a) {
  return function (a) {
    return a + 5;
  }
}

const func = add5(3) // add is finished here

// func still has access to `a`
func()

// same as 
add5(3)()

// output ??
```

## Higher-Order Functions (**HOF**)

Functions that take other functions as arguments and/or return functions as their result. Many built-in functions in JavaScript are HOFs.

```js
function multiplyBy(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
const triple = multiplyBy(3);

console.log(double(5)); // Output: ?
console.log(triple(5)); // Output: ?
```

## Anonymous Functions

Functions :u[without a name] that are defined as expressions rather than declarations.

```js
const sum = function(param1, param2) {
  // TODO:
};
```

## Arrow Functions

A shorthand syntax for writing functions using the **`=>`** operator. They are often used in place of anonymous functions.

An interesting aspect of arrow functions it that they preserve the parent context (\`this\`) in which they are declared.

```js
const arrowSum = (param1, param2) => {
  // TODO
};


function todo() {

  const divideCtx = () => {
    // ...
    const self = this; // this or self is the context of todo function

  }

 const divide = function noCtx() {
    // ...
    const self = this; // this or self is the context of noCtx function
  }
  
}
```

## IIFE: Immediately Invoked Function Expressions

Functions that are created and invoked immediately.

```js
(function() {
  var message = "Hello!";
  console.log(message);
})();

// Output: "Hello!"

(() => {
  // …
})();
```

zar

*   **Function Hoisting**: A behavior in JavaScript where function declarations are moved to the top of their scope, allowing them to be used before they are defined. **Hoisting works only for function declarations, it does not work for variables or function expressions.**

    ```js
    // This will work
    sayHello(); // Output: ??

    function sayHello() {
      console.log("Hello, World!");
    }

    // This will NOT work
    console.log(abc);

    const abc = "This unit is amazing!";

    console.log(abc);

    // This will NOT work
    sayExpHello(); // Output: ??

    const sayExpHello = function () {
      console.log("Hello, World!");
    }
    ```

*   **This Keyword**: A reference to the current object that the function is attached to. Its value changes depending on how the function is called.

    ```js
    const person = {
      firstName: "Sarah",
      lastName: "Haras",
      fullName: function() {
      // see the use of `this.firstName` to access variables inside person
        console.log(this.firstName + " " + this.lastName);
      }
    };

    person.fullName(); // Output: ??
    ```

*   **Default Function Parameters**: Parameters with default values that are used when the parameter is not passed to the function.

    ```js
    function greet(name = 'Laval') {
      console.log(`Hello from ${name}!`);
    }

    greet(); // Output: Hello from Laval!
    greet('Le Mans'); // Output: Hello from Le Mans! 
    ```

*   **Rest and Spread Operators**: The \`**`` ...` ``** syntax that allows functions to accept an arbitrary number of arguments or to spread out an array into individual arguments.

    ```js
    // rest
    function sum(...numbers) {
      return numbers.length;
    }

    console.log(sum(1, 2, 3, 4, 5)); // Output: ??

    var arr1 = [1, 2, 3];
    var arr2 = [4, 5, 6];

    // spread
    var merged = [...arr1, ...arr2];
    console.log(merged); // Output: ??
    ```

*   **Pure Functions**: Functions that always produce the same output given the same input and do not have any side effects.

    ```js
    // This is pure
    function double(x) {
      return x * 2;
    }

    // always the output will the same
    console.log(double(5)); // Output: ??

    const speed = 3;

    // is it pure?
    function distance(time = 4) {
      return speed * time;
    }

    // always the output will the same?
    console.log(distance(5)); // Output: ??
    ```

    **Currying**: The process of transforming a function that takes multiple arguments into a series of functions that each take a single argument. A way to ensure that a function is pure with a single responsibility.

    ```js
    function multiply(a, b, c) {
      return a * b * c;
    }

    function curryMultiply(fn) {
      return function(a) {
        return function(b) {
          return function(c) {
            return fn(a, b, c);
          };
        };
      };
    }

    console.log(curryMultiply(4)(2)(3)); // Output: ??
    ```

*   **Function Factories**: Functions that return other functions, allowing for the creation of reusable functions with partially applied arguments or other configurations.

    ```js
    function makeGreeting(language) {
      return function(firstName, lastName) {
        if (language === "en") {
          console.log("Hello, " + firstName + " " + lastName + "!");
        } else if (language === "es") {
          console.log("¡Hola, " + firstName + " " + lastName + "!");
        } else if (language === "fr") {
          console.log("Bonjour, " + firstName + " " + lastName + "!");
        }
      };
    }

    var sayFrHello = makeGreeting("fr");
    var sayEsHello = makeGreeting("es");

    sayFrHello("Sarah", "Haras"); // Output: ??
    sayEsHello("Alex", "Perez"); // Output: ??
    ```

*   **Recursion**: A technique where a function calls itself in order to solve a problem by breaking it down into smaller, similar problems.

    ```js
    function factorial(n) {
      if (n === 0) {
        return 1;
      } else {
        return n * factorial(n - 1);
      }
    }

    console.log(factorial(5)); // Output: ??
    ```

    *   **Memoization**: A technique where a function's results are cached to improve performance when the function is called with the same arguments.

        ```js
        // memo is a cache object
        function fibonacci(n, memo = {}) {
          if (memo[n]) {
            return memo[n];
          }

          if (n <= 2) {
            return 1;
          }

          const result = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);

          memo[n] = result;
          return result;
        }

        console.log(fibonacci(10)); // Output: ??
        ```

## Other Avanced Concepts

*   **Generator Functions**: Functions that can be paused and resumed, allowing for asynchronous programming without the use of callbacks.

    ```js
    // Todo: provide and example of Generator
    ```

*   **Decorators**: Functions that modify the behavior of other functions without changing their original code.

    ```js
    // Todo: provide and example of Decorators
    ```

*   **call:** The call method is used to call a function with a specified **`this`** value and arguments provided individually.

*   **apply**: The apply method is similar to call, but it takes an array of arguments instead of individual arguments.

*   **bind**: The bind method creates a new function that, when called, has its this keyword set to the provided value.