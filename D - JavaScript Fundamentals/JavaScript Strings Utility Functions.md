---
type: NoteCard
tags: []
---

# JavaScript Strings Utility Functions
split: This function is used to split a string into an array of substrings based on a specified separator.

```javascript
const str = "This is a sample string";
const words = str.split(" ");
console.log(words); // Output: ??
```

trim: Removes whitespace from both ends of a string.

```js
const str = "  Hello, World!  ";
const trimmedStr = str.trim();
console.log(trimmedStr); // ??
```

substring or slice: Extracts a part of a string and returns the extracted part.

```js
const str = "Hello, World!";
const substring = str.substring(0, 5);
console.log(substring); /// ??
```

replace or replaceAll: Replaces the first occurrence of specified values in a string with a new value or replaceAll the occurrences.

```js
const str = "Hello, World!";
const replacedStr = str.replace("World", "Universe");
console.log(replacedStr); // ..

const replacedAllStr = str.replaceAll("l", "L");
console.log(replacedAllStr); // ..
```

match or search: Searches a string for a specified pattern and returns the matches as an array.

```js
const str = "The quick brown fox jumps over the lazy dog";
const matches = str.match(/[A-Z]/g);
console.log(matches); // ...
```

search: Searches a string for a specified value and returns the position of the first occurrence.

```js
const str = "The quick brown fox jumps over the lazy dog";
const position = str.search("fox");
console.log(position); // ...
```

toUpperCase or toLowerCase: Converts a string to uppercase or lowercase.

```js
const str = "Hello, World!";
const uppercaseStr = str.toUpperCase();
console.log(uppercaseStr); // ..


const lowercaseStr = str.toLowerCase();
console.log(lowercaseStr); // ..
```

charCodeAt: Returns the Unicode value of the character at a specified position in a string.

```js
const str = "Hello";
const unicodeValue = str.charCodeAt(1);
console.log(unicodeValue); // ...
```

fromCharCode: Converts Unicode values to characters.

```js
const char = String.fromCharCode(101);
console.log(char); // ..
```