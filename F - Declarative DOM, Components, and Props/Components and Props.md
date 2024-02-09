---
type: NoteCard
tags: []
---

# Components and Props
Building on the concept of :ref[Declarative DOM]{path='/notes'}, modern frameworks allow us to create reusable :u[user interface] elements (UI), and customize their :u[appearance] and :u[interactivity] **declaratively**. This is where **components** and their **properties** (also known as **props** for short) come into play.

Reusing code is often beneficial. Modern web frameworks provide a set of features to create components. Components are like custom HTML elements (e.g., `<my-custom-menu>`). They are similar to native HTML elements <`div>`, `<span>`, etc. In other words, components allow us to create what we have seen previously, which is, you guessed it.. right! The :u[DOM].

In addition to creating the DOM, components can have behaviors as well. Behaviors define how components manage their states and how they respond to user inputs.

In the modern web, components are the building blocks of interactive user interfaces (UI). An interesting feature of modern components is that they encapsulate HTML, JS, and CSS all in one file (so-called :u[single file component] or SFC). Because of this encapsulation, we can create, combine, and reuse small components to construct more complex UIs. It is often easier to reuse and maintain an isolated (decoupled) component that defines its DOM (HTML), behavior and interactivity (JS), and appearance (style or CSS) all in one place.

Note that it is possible to create web components using DOM native APIs in JS, such as custom elements, shadow DOM, and HTML templates (\<template> and \<slot>). If you are interested in learning more about native custom elements, please refer to this MDN documentation (<https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements>). We will touch on this very briefly in our lab on this topic. However, for the most part, we will focus on web components using frameworks, such as React, Vue, and Svelte.

In sum, the encapsulation of JS and HTML to create components enables us to:

1.  Render DOM based on (or similar) JS APIs and
2.  Pass properties to components (called props for short)

Props allow us to build dynamic UI, simply because props often represent values of JS objects that are interpolated and rendered as DOM by modern frameworks.

Props can be passed down the components tree, i.e., from one component to another.