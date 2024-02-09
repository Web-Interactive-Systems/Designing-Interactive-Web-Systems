---
type: NoteCard
tags: []
---

# JavaScript Array Utility Functions
**map**: applies a function to each element of an array and returns a new array with the results.

```js
const arr1 = [1, 2, 3];
const arr2 = arr1.map(num => num * 2);
console.log(arr2); // ???
```

**filter**: creates a new array with all elements that pass a test implemented by the provided function.

```js
const arr1 = [1, 2, 3];
const arr2 = arr1.filter(num => num % 2 === 0);
console.log(arr2); // ??
```

**reduce**: applies a function to each element of an array, resulting in a single output value.

```js
const arr1 = [1, 2, 3];
const sum = arr1.reduce((acc, num) => acc + num, 0);
console.log(sum); // ??
```

**forEach**: executes a provided function once for each array element.

```js
const arr1 = [1, 2, 3];
arr1.forEach(num => console.log(num));
// ?
```

**find**: returns the value of the first element in an array that satisfies the provided testing function

```js
const arr1 = [1, 2, 3];
const num = arr1.find(num => num > 1);
console.log(num); // ?
```

**some**: tests whether at least one element in the array passes the test implemented by the provided function.

```js
const arr1 = [1, 2, 3];
const some = arr1.some(num => num % 2 === 0);
console.log(some); // ?
```

**every**: tests whether all elements in the array pass the test implemented by the provided function.

```js
const arr1 = [1, 2, 3];
const every = arr1.every(num => num % 2 === 0);
console.log(every); // ?
```

**concat**: returns a new array that is the result of joining two or more arrays.

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
const arr3 = arr1.concat(arr2);
console.log(arr3); // ??
```

**slice**: returns a portion of an array into a new array.

```js
const arr1 = [1, 2, 3];
const arr2 = arr1.slice(0, 2);
console.log(arr2); // ??
```

**splice**: changes the contents of an array by removing or replacing existing elements and/or adding new elements.

```js
const arr1 = [1, 2, 3];
arr1.splice(1, 1, 4, 5);
console.log(arr1); // ??
```

**push**: adds one or more elements to the end of an array and returns the new length of the array.

```js
const arr1 = [1, 2, 3];
const length = arr1.push(4, 5);
console.log(length); // ??
console.log(arr1); // ??
```

**pop**: removes the last element from an array and returns that element.

```js
let fruits = ["apple", "banana", "orange"];

let removedFruit = fruits.pop(); // removes "orange" from the end of the array and returns it

console.log(fruits); // ??
console.log(removedFruit); // ??
```

**shift**: Removes the first element from an array and returns that element.

```js
const numbers = [1, 2, 3, 4, 5];
const firstNumber = numbers.shift();

console.log(numbers); // ??
console.log(firstNumber); // ??
```

**unshift**: Adds one or more elements to the beginning of an array and returns the new length of the array.

```js
const numbers = [2, 3, 4, 5];
const newLength = numbers.unshift(1);

console.log(numbers); // ??
console.log(newLength); // ??
```

**indexOf**: Returns the first index at which a given element can be found in an array, or -1 if it is not present.

```js
const numbers = [1, 2, 3, 4, 5];
const index = numbers.indexOf(3);

console.log(index); // ??
```

**lastIndexOf**: Returns the last index at which a given element can be found in an array, or -1 if it is not present.

```js
const numbers = [1, 2, 3, 4, 2, 5];
const index = numbers.lastIndexOf(2);

console.log(index); // ??
```

**includes**: Determines whether an array includes a certain value among its entries, returning true or false as appropriate.

```js
const numbers = [1, 2, 3, 4, 5];
const hasThree = numbers.includes(3);

console.log(hasThree); // ??
```

**join**: This function is used to join all elements of an array into a string using a specified `separator`.

```js
const words = ["This", "is", "a", "sample", "string", "every", "word", "is", "separated"];
const str = words.join(", ");
console.log(str); // ...
```