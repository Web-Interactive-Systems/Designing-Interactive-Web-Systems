---
type: NoteCard
tags: []
---

# Callbacks and Promises in JavaScript
Callbacks: Callbacks are functions that are passed as arguments to other functions and are called when the asynchronous operation completes. They are commonly used to handle events or perform some action after an asynchronous task has completed.

```js
function fetchData(url, callback) {
  const xhr = new XMLHttpRequest();
  xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
      callback(xhr.responseText);
    }
  }
  xhr.open('GET', url);
  xhr.send();
}

function processData(data) {
  console.log(`Processed data: ${data}`);
}

fetchData('https://example.com/data', processData);
```

> `fetchData` fetches data from a URL using XMLHttpRequest, and takes a callback function as its second parameter. The `processData` function is the callback that is called when the data is fetched successfully.

Promises: Promises are objects that represent the eventual completion or failure of an asynchronous operation and provide a way to handle the result. Promises can be in one of three states: pending, fulfilled, or rejected.

```js
// creating a promise
const promise = new Promise(function(resolve, reject) {
  // do some asynchronous operation
  setTimeout(function() {
      const result = 'some result';
      if (result) {
        resolve(result);
      } else {
        reject('error');
      }
    }, 2000);
});
```

Promise.all: wait for multiple Promises to complete

```js
// Promise.all
const promise1 = Promise.resolve('Promise 1');
const promise2 = new Promise(function(resolve, reject) {
  setTimeout(function() {
    resolve('Promise 2');
  }, 2000);
});
const promise3 = new Promise(function(resolve, reject) {
  setTimeout(function() {
    resolve('Promise 3');
  }, 1000);
});

Promise.all([promise1, promise2, promise3])
  .then(function(results) {
    console.log(results);
  }).catch(function(error) {
    console.error(error);
  });

promise.then(function(result) {
  console.log(result);
}).catch(function(error) {
  console.error(error);
});
```

Chaining: Promises can be chained together to create more complex operations. This allows developers to execute a series of asynchronous tasks in a specific order, where the result of one operation is passed to the next.

```js
function fetchJson(url) {
  return fetch(url).then(function(response) {
    return response.json();
  });
}

function getUserInfo(userId) {
  return fetchJson(`https://jsonplaceholder.typicode.com/users/${userId}`);
}

function getUserPosts(userId) {
  return fetchJson(`https://ajsonplaceholder.typicode.com/address?id=${userId}`);
}

getUserInfo(1)
  .then(function(user) {
    console.log(`User info: ${JSON.stringify(user)}`);
    return getUserPosts(user.id);
  }).then(function(posts) {
    console.log(`User posts: ${JSON.stringify(posts)}`);
  }).catch(function(error) {
    console.error(error);
  });
```

Async/await: Async/await is a newer way of handling asynchronous code that was introduced in ES8. It provides a way to write asynchronous code that looks and behaves more like synchronous code.

```js
// example 1
async function fetchUsers() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// example 2
const fs = require('fs');

async function readFile() {
  try {
    const data = await fs.promises.readFile('file.txt', 'utf8');
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

// example 3
function fetchData(url) {
  return fetch(url).then(response => response.json());
}

async function fetchAll() {
  const urls = [
    'https://jsonplaceholder.typicode.com/posts',
    'https://jsonplaceholder.typicode.com/comments',
    'https://jsonplaceholder.typicode.com/users'
  ];

  const [posts, comments, users] = await Promise.all(urls.map(fetchData));

  console.log(posts);
  console.log(comments);
  console.log(users);
}
```

Error handling: In asynchronous programming, error handling is an important concept. Errors can occur at any time during the asynchronous operation, so it is important to have a mechanism in place to handle them. This can be done through the use of try/catch blocks, by providing error-handling functions as callbacks or by using catch with promises.

```js
function fetchData() {
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      const data = [1, 2, 3, 4, 5];
      if (data.length > 0) {
        resolve(data);
      } else {
        reject(new Error("No data"));
      }
    }, 2000);
  });
}

fetchData()
  .then(function(data) {
    console.log("Data:", data);
  })
  .catch(function(error) {
    console.log("Error:", error);
  });
```