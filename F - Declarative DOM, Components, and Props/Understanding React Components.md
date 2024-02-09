---
type: NoteCard
tags: []
---

# Understanding React Components
In React, an application is composed of one or more components. A component is a reusable self-contained block of code that encapsulates **HTML**, **CSS**, and **JavaScript** that work together to create a view (part of the user interface). This includes buttons, headings, images, input texts, and so forth. A react component is written into a javascript file **.js or .jsx.**

JSX is a syntax extension for JavaScript that lets us write HTML-like markup inside a JavaScript file. JSX is enabled by React toolchains (in our labs that is vite).

We already seen different components in example app that we have created.

Root component `main.js`: this a the root component that will attach (mount) the app to the HTML.

## Root Component

```js
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

```js
ReactDOM.createRoot(document.getElementById('root'))
```

::::cal
The above code will attach the app to the `root` element. Find the root element inside **index.html**.

::::

```js
<React.StrictMode>
```

::::cal
**StrictMode**: let us find common bugs in our components early during development.

::::

## App Component (Count)

```js
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <div className="App">
      <div>
        <a href="https://vitejs.dev" target="_blank">
          <img src="/vite.svg" className="logo" alt="Vite logo" />
        </a>
        <a href="https://reactjs.org" target="_blank">
          <img src={reactLogo} className="logo react" alt="React logo" />
        </a>
      </div>
      <h1>Vite + React</h1>
      <div className="card">
        <button onClick={() => setCount((count) => count + 1)}>
          count is {count}
        </button>
        <p>
          Edit <code>src/App.jsx</code> and save to test HMR
        </p>
      </div>
      <p className="read-the-docs">
        Click on the Vite and React logos to learn more
      </p>
    </div>
  )
}

export default App
```

::::cal
*   Notice the imports, including CSS
*   Notice the default export of the App
*   Notice how the component App returns an HTML
*   Notice the use of className to link CSS to parts of the HTML
*   Notice how an event handler is attached to the count button
*   Notice how the variable count is “binded” to the HTML, `count is {count}`

::::