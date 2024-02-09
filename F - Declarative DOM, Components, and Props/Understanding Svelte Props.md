---
type: NoteCard
tags: []
---

# Understanding Svelte Props
Similar to React, props are read-only data passed down from a parent component to a child component. They are used to customize the behavior and appearance of a component. Props can be data attributes (values) or functions.

```js
<!-- ParentComponent.svelte -->
<script>
  import ChildComponent from './ChildComponent.svelte';

  const myProp = 'Hello, world!';
</script>

<ChildComponent propname={myProp} />
```

```js
<!-- ChildComponent.svelte -->
<script>
  export let propname;
</script>

<p>{propname}</p>
```

In this example, myProp is defined in the parent component and passed down to the child component using the propname={myProp} syntax.

The child component then receives the prop using the **export** let propname syntax and can use it in its template.