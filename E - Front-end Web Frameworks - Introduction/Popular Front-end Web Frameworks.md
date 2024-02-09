---
type: NoteCard
tags: []
---

# Popular Front-end Web Frameworks
React, Angular, Vue, and Svelte are popular front-end web development frameworks. They allow developers to create dynamic and interactive web applications with ease. Each of these tools has its own strengths and features, but they all share a common goal. They aim for simplifying the process of building complex user interfaces. To achieve this, modern framework offer key core functionalities to developers.

## Component-based architecture

Component-based architecture allows developers to break down the application into reusable, modular components, which can be easily composed to build more complex user interfaces (UIs).

Modern frameworks provide way to create web component declaratively, using html language.

## Virtual DOM (VDOM)

DOM (**Document Object Model)** is the objects of a web page. Basically, the DOM of a web page represents the structure and content of the web page. Web clients, such as browsers, render (display) the DOM of web pages.

The DOM has many APIs. They offer a wide range of functions to perform various operation on the web, such as creating and manipulating DOM elements (div, span, text, css styles, etc.), handling events, getting data from forms, streaming video, recording audio, activating a webcam feed, etc. Doing DOM operation is complex and verbouse.

Modern frameworks aim to provide a better (often simplied) way of manipulating the DOM.

Some frameworks, such as ReactJs, rely on a Virtual DOM. VDOM is a virtual lightweight duplicate representation of the real DOM. VDOM-based frameworks store VDOM in memory to improve performance of rendering and update the DOM.

In other words, when the real DOM needs to change

*   VDOM is used to perform all operations needed to update the real DOM,

    *   this is fast, because it is done on a lightweight virtual DOM in memory

*   then, a reconsilation is performed to change the real DOM based on the difference between the VDOM and real DOM

## State management and reactivity

State management and reactivity are a set of APIs and patterns provided by modern frameworks for

*   Managing the application state and data flow between different components
*   Reactively updating the DOM (UIs) when the data of the application changes

Imagine, we are building a todo list app. The app should

1.  store the items (todos) that a users will add and
2.  show the items in a list

Using state management and reactitivity, we can define an array of items in the state. When the the user add a new item (todo), then, we add the item to the array in the state. And because the state is reactive, when state array is updated the framework will automatically change the user interface (without refereching the web page).

Routing: Routing mechanisms for managing the application's navigation flow, between different views or pages.

Server-side rendering: Provide the ability to render the application on the server side, which can improve the application's initial load time as well as SEO.

Tooling and ecosystem: A set of tooling, such as build tools, code generators, and testing frameworks, and an ecosystem of third-party libraries and plugins to extend their functionality.