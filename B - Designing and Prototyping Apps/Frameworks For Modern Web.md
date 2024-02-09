---
type: NoteCard
tags: []
---

# Frameworks For Modern Web
Frameworks are the cornerstone of the modern web. After all, “what is a framework.”

## What is a framework?

> A framework is a reusable set of libraries or classes in software. To help developers focus their work on higher-level tasks, a framework provides a functional solution for lower-level elements of coding. While a framework might add more code than is necessary, it also provides a reusable pattern to speed up development.
>
> — source:

## Why do frameworks exist?

Nowadays there is a high demand for sophisticated web apps. Building robust apps is challenging. Consider a simple to-do list app. The app should allow users to manage tasks, such as:

*   Display
*   Add
*   Find
*   Edit
*   Delete

**In addition, the app should reliably:**

*   Track and update the data underlying the app — known as the state
*   Update the UI when the state changes
*   Perform background non-blocking operations (e.g., using web workers), for example to save assets in users’ browsers
*   Work offline
*   Sync data with multi-devices of the user, such mobile phone, desktop, and laptop
*   Perform caching (e.g., using web workers) to speed up processing
*   And, many more

While it is possible to handle such needs without without frameworks, it can be challenging to do so.

## The web can be challenging

While a simple to-do list app might seem easy to design and implement, advanced features, such as the ones mentioned above, can be difficult.

Implementing such features without frameworks (meaning from scratch) can be challenging, simply because manipulating UI or DOM and native APIs using plain javascript is

*   Tedious
*   Verbose
*   Requires a lot amount of low-level code
*   Hard to maintain

## Example of to-do list app without frameworks

```js
const state = {tasks: [
  {
    id: "todo-0",
    status: "doing",
    name: "Learn modern web frameworks",
  },
]};
```

```js
function buildTodoItemEl(id, name) {
  const item = document.createElement("li");
  const span = document.createElement("span");

  const textContent = document.createTextNode(name);

  span.appendChild(textContent);

  item.id = id;
  item.appendChild(span);
  item.appendChild(buildDeleteButtonEl(id));

  return item;
}
```

```js
function buildDeleteButtonEl(id) {
  const button = document.createElement("button");
  const textContent = document.createTextNode("Delete");

  button.setAttribute("type", "button");
  button.appendChild(textContent);

  return button;
}
```

```js
function renderTodoList() {
  const frag = document.createDocumentFragment();
  state.tasks.forEach((task) => {
    const item = buildTodoItemEl(task.id, task.name);
    frag.appendChild(item);
  });

  while (todoListEl.firstChild) {
    todoListEl.removeChild(todoListEl.firstChild);
  }
  todoListEl.appendChild(frag);
}
```

## Question

> *Why do frameworks exists?*

## Frameworks solve many problems

Frameworks exist to provide a better developer experience. Each framework provides a toolchain to:

*   Managing the lifecycle of web apps from development to dependencies to production
*   Streamlining and speeding up the creation and manipulation of UI

> Frameworks enable developers to focus on building value for their apps rather than struggling with configuration and best practices of web development

## Question

> *What are the building blocks for modern web apps?*

## Modern web apps ecosystem:

Modern apps rely on many building blocks, including:

*   Modern toolchain or tooling

    *   Text editors and IDEs
    *   Package manager
    *   Builders/packagers: such as parcel, esbuild, vite, webpack
    *   Command line (a cli)
    *   Safety net: linters, coding styles, code formatters, such as eslint, tslint, and prettier
    *   Transformers, such as babel, typescript, postcss, minification

*   Declarative DOM systems, such as React, Vue, Svelte

*   Compartmentalization: modular, and components-based architecture

*   State management

*   Store management

*   Event management

*   Styling

*   Routing

*   Testing

*   UI design system

In the following sections with learn more about each of these building blocks.

## An equivalent of a to-do app using a modern framework

```js
<ul>
  <li v-for="task in tasks" v-bind:key="task.id">
    <span>{{task.name}}</span>
    <button type="button">Delete</button>
  </li>
</ul>
```

## Question

> *What are the modern web frameworks that you are aware of?*

## Current modern web frameworks

There are a number of frameworks for the modern web. At the time of this writing, the big ones are (in alphabetical order):

*   React
*   Vue
*   Svelte
*   Angular
*   Qwik

Others that bring integrated approach (API, server-first, zero-js first, SSR, and many more) to the web. These framework are best suitable for content-rich web apps:

*   Nextjs on the top of React
*   Astro on the top of React
*   Nuxjs on the top of Vuejs
*   Sveltekit on the top of Svelte
*   Bun a meta framework

In this course, we will have the chance to learn and practice React, Vue, and Svelte. We will also have the chance to work on a projet using Astro.

## Question

> *What are the challengs of web frameworks?*

## Challenges with modern framework

*   There is a huge number of frameworks. They differ in many ways.

*   At times it can be challenging to find the right frameworks for the job at hand.

*   In general look at forums (documentations, github, discord servers, and others) about:

    *   Specific offerings of a framework
    *   Amount of configuration required to use the framework
    *   Learning curve required to master the framework

## Tools and Downloads

The following tools are recommended for this course. Try to install them to follow along.

*   **Visual Studio Code** for JS Development
*   **Node 18 and NPM 8** for React Development
*   **Postman** for API Exploration
*   **Git** for Version Control/Submission
*   **Github**