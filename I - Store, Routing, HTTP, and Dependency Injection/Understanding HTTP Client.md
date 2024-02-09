---
type: NoteCard
tags: []
---

# Understanding HTTP Client
HTTP Client is part of almost all modern web applications. It allows web apps to communicate with external servers and APIs over the internet. It mainly enables apps to retrieve data from and send data to remote sources, and update UIs accordingly.

**Fetch API**: Fetch API is a modern interface for fetching resources over the network. It provides a more flexible and powerful way to send HTTP requests and handle responses using Promises. With Fetch API, web apps can send requests with different methods, headers, and bodies, and receive responses in various formats, such as JSON, text, or blobs.

```js
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// a more complete example
import React, { useState, useEffect } from "react";

function TodoList() {
  const [todos, setTodos] = useState([]);

  useEffect(() => {
    async function fetchTodos() {
      try {
        const response = await fetch("https://jsonplaceholder.typicode.com/todos");
        const data = await response.json();
        setTodos(data);
      } catch (error) {
        console.error(error);
      }
    }
    fetchTodos();
  }, []);

  return (
    <div>
      <h2>Todo List</h2>
      <ul>
        {todos.map((todo) => (
          <li key={todo.id}>{todo.title}</li>
        ))}
      </ul>
    </div>
  );
}

export default TodoList;
```

**Axios**: Axios is a popular HTTP client library for JavaScript that simplifies the process of sending HTTP requests and handling responses. It supports all modern browsers and provides various API for making HTTP calls using REST and Graphql.

```js
import axios from 'axios';

// make a GET request to fetch all todos
axios.get('https://jsonplaceholder.typicode.com/todos')
  .then(response => {
    console.log(response.data);
    // set the todos state with the fetched data
    setTodos(response.data);
  })
  .catch(error => {
    console.log(error);
  });

// make a PUT request to update a todo
axios.put(`https://jsonplaceholder.typicode.com/todos/${id}`, {
    title: 'Updated Todo',
    completed: true
  })
  .then(response => {
    console.log(response.data);
    // update the todo in the todos state
    setTodos(todos.map(todo => todo.id === id ? response.data : todo));
  })
  .catch(error => {
    console.log(error);
  });

// make a DELETE request to delete a todo
axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
  .then(response => {
    console.log(response.data);
    // remove the deleted todo from the todos state
    setTodos(todos.filter(todo => todo.id !== id));
  })
  .catch(error => {
    console.log(error);
  });
```

**RESTful API**: REST (Representational State Transfer) is a design pattern for creating web APIs that follow specific principles, such as using HTTP methods for CRUD operations, using URLs for resource identification, and using headers for metadata.

```js
const express = require('express');
const app = express();

app.get('/todos/:id', (req, res) => {
  const id = req.params.id;
  const todo = { id: id, title: 'Finish project', completed: false };
  res.json(todo);
});

app.listen(3000, () => console.log('Server started on port 3000'));
```