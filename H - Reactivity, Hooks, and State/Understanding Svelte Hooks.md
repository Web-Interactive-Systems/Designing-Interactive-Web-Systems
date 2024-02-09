---
type: NoteCard
tags: []
---

# Understanding Svelte Hooks
Svelte has concepts similar to React hooks.

The equivalent useState for Svelte is the Reactivity concept of Svelte.

**onMount**: This is similar to the useEffect hook in React and allows developers to perform side effects when a component is mounted.

```js
 <script>
      	import { onMount } from 'svelte';

      	let photos = [];

      	onMount(async () => {
      		const res = await fetch(`/tutorial/api/album`);
      		photos = await res.json();
      	});
      </script>
```

**onDestroy**: This is similar to the useEffect hook with a cleanup function in React and allows developers to perform cleanup when a component is unmounted.

```js
 <script>
      	import { onDestroy } from 'svelte';

      	let counter = 0;
      	const interval = setInterval(() => counter += 1, 1000);

      	onDestroy(() => clearInterval(interval));
      </script>
```

**beforeUpdate**: is executed before the component is updated, but after the props have been received and before the new state has been computed. This means that you can use this method to access the previous state or props before they are updated.

**afterUpdate**: is executed after the component has been updated, but before the DOM has been updated. This means that you can use this method to access the new state or props, and update any other properties that may be dependent on them.

```js
<script>
        let count = 0;

        function handleClick() {
          count += 1;
        }

        function beforeUpdate() {
          console.log(`count before update: ${count}`);
        }

        function afterUpdate() {
          console.log(`count after update: ${count}`);
        }
      </script>

<button on:click={handleClick}>
        Clicked {count} times
      </button>
```

```js

      let div;

      let autoscroll;


      beforeUpdate(() => {
      	autoscroll = div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight - 20);
      });


      afterUpdate(() => {
      	if (autoscroll) div.scrollTo(0, div.scrollHeight);
      });
```