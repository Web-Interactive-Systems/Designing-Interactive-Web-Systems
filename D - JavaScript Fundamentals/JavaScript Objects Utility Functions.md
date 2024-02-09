---
type: NoteCard
tags: []
---

# JavaScript Objects Utility Functions
Object.keys(): Returns an array of the object's own enumerable properties' names.

```js
const obj = { name: 'bar', age: 30 };

const keys = Object.keys(obj);

console.log(keys); // ??
```

Object.values(): Returns an array of the object's own enumerable property values.

```js
const obj = { name: 'bar', age: 30 };

const values = Object.values(obj);

console.log(values); // ??
```

Object.entries(): Returns an array of the object's own enumerable properties as [key, value] pairs.

```js
const obj = { name: 'foo', age: 30 };

const entries = Object.entries(obj);

console.log(entries); // ???
```

Object.assign(): Copies the values of all enumerable properties from one or more source objects to a target object, and returns the target object.

```js
const target = { name: 'Sarah', age: 30 };

const source = { age: 40, gender: 'human' };

const result = Object.assign(target, source);

console.log(result); // ...
```

Object.freeze(): Freezes an object, preventing new properties from being added to it and existing properties from being removed or changed.

```js
const obj = { name: 'bar', age: 30 };

Object.freeze(obj);

obj.age = 40; // what's the effect of this?

console.log(obj); // ..
```

Object.seal(): Seals an object, preventing new properties from being added to it and marking all existing properties as non-configurable.

```js
const obj = { name: 'bar', age: 30 };

Object.seal(obj);

delete obj.age; // what's the effect of this?

obj.gender = 'other'; // what the effect of this?

console.log(obj); // ??
```

[Object.is](http://object.is/)(): Determines whether two values are the same value. Equivalent to the triple equals operator (===), except that NaN is considered equal to NaN.

```js
console.log(Object.is(1, 1)); // ?

console.log(Object.is('foo', 'foo')); // ?
console.log(Object.is({}, {})); // ?

console.log(Object.is(NaN, NaN)); // ?
```

JSON.stringify(): Converts a JavaScript object or value to a JSON string.

```js
const obj = { name: 'John', age: 30 };

const json = JSON.stringify(obj);

console.log(json); // ??
```

JSON.parse(): Parses a JSON string and returns a JavaScript object or value.

```js
const json = '{"name":"John","age":30}';

const obj = JSON.parse(json);

console.log(obj); // ??
```