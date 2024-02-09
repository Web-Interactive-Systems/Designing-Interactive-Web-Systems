---
type: NoteCard
tags: []
---

# Understanding Svelte Data Binding, Rendering, View State
Data binding is the way to keep the state of the application synchronized with the view (what is displayed in the real DOM). Whenever there is a change in the state, the view gets updated automatically.

There are two types of data binding in Svlete: One-way data binding and Two-way data binding.

## One-way data binding

In one-way data binding, the data flows in a single direction, from the state to the view. Any changes made to the state will update the view.

```js
 <script>
        let name = 'world';
      </script>


      <main>
        <h1>Hello, {name}!</h1>
      </main>
```

## Two-way data binding

In two-way data binding, the data flows in both directions, from the state to the view and from the view to the state. Any changes made to the state or the view will update the other.

```js
<script>
        let name = 'world';
      </script>


      <input value={name}>


      <h1>Hello {name}!</h1>
```

## Svelte's Reactivity