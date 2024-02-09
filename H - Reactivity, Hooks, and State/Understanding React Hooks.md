---
type: NoteCard
tags: []
---

# Understanding React Hooks
React Hooks are a set of functions provided by React that allow developers to use state and lifecycle methods in functional components. React has a set of built-in hooks and provides a simple API to create hooks. The most important hooks provided by React are:

useState: The useState Hook allows components to have state without using class components. It takes an initial state value and returns an array with the current state value and a function to update that value.

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(count + 1);
  }

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={increment}>Click me</button>
    </div>
  );
}
```

useEffect: The useEffect Hook allows components to have lifecycle methods without using class components. useEffect tacks a callback and an array of dependencies. The callback is executed after the component has been mounted to the DOM. **`useEffect`** runs after the first render and after every update in the values of the dependencies (i.e., when the dependencies’ state changes).

```js
import React, { useState, useEffect } from 'react';

function Timer() {
  const [time, setTime] = useState(0);

  useEffect(() => {
    const intervalId = setInterval(() => {
      setTime(prevTime => prevTime + 1);
    }, 1000);

    return () => {
      clearInterval(intervalId);
    };
  }, []);

  return <div>{time} seconds</div>;
}
```

useContext: The useContext Hook allows components to access context values without using the Context API. It takes a context object and returns the current value of that context.

```js
// UserContext.js

import { createContext } from "react";

const UserContext = createContext({
  user: {
    name: "Guest",
    email: "guest@example.com",
  },
});

export default UserContext;


// UserProfile.js

import React, { useContext } from 'react';
import { UserContext } from './UserContext';

function UserProfile() {
  const { user } = useContext(UserContext);

  return (
    <div>
      <h2>{user.name}</h2>
      <p>{user.email}</p>
    </div>
  );
}

export default UserProfile;
```

useRef: The useRef Hook allows components to access and modify DOM nodes or any mutable value without re-rendering the component.

```js
import React, { useRef } from 'react';

function TextInput() {
  const inputRef = useRef(null);

  function handleClick() {
    inputRef.current.focus();
  }

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleClick}>Focus input</button>
    </div>
  );
}
```

useReducer: The useReducer Hook allows components to have complex state and actions without using class components. It takes a reducer function and an initial state value, and returns the current state value and a dispatch function to update that state.

```js
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
}
```