---
type: NoteCard
tags: []
---

# Lifecycle and Side-effects
Components have lifecycles. They can mount, update, or unmount. A component:

*   **Mounts** when it’s added to the screen
*   **Updates** when it receives new props or state.
*   **Unmounts** when it’s removed from the screen.

Using components lifecycles, we can perform more fine grounded control of the rendering. For example, we can wait until a page is mounted to the screen before rendering a list of items or free resources and clean event listeners when a component is unmounted from the screen.

Native DOM offers ways to interact with a component lifecycle. Here is an example:

    class Circle extends HTMLElement {
         // ..

        constructor() {
          super();

         // shadow dom
         // ...
        }

        connectedCallback() {
          console.log('Mount: Circle added to page.');
          // update ....
          updateStyle(this);
        }

        disconnectedCallback() {
          console.log('Unmout: Circle removed from page.');
        }

        attributeChangedCallback(name, oldValue, newValue) {
          console.log('Update: Circle attributes changed.');
         // update ...
          updateStyle(this);
        }
      }

Modern frameworks provide APIs to interact with a component's lifecycle.

With React functional components, we can use the effect `useEffect`

    function App() {
      // State for our component
      const [count, setCount] = useState(0);

      console.log('Render App');

      // Mounting phase: componentDidMount
      useEffect(() => {
        // Add event listeners, perform initial data fetching, etc.
        console.log('Component did mount');
      }, []); // Empty dependency array means this effect runs only once on mount

      // Updating phase: componentDidUpdate
      useEffect(() => {
        // Handle state or prop changes here
        console.log('Component did update');
        return () => {
          // Clean up resources (e.g., remove event listeners)
          console.log('Component will unmount');
        };
      }, [count]); // Runs whenever 'count' changes

      return (
        <div>
          <h1>Component Lifecycle Example</h1>
          <p>Count: {count}</p>
          <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
      );
    }

Vue provides similar [APIs](https://vuejs.org/api/composition-api-lifecycle.html). Here is an example:

    <script setup>
    import { onBeforeMount, onMounted, onUpdated, onUnmounted } from "vue";

    onBeforeMount(() => {
      console.log('onBeforeMount');
    });

    onMounted(() => {
      console.log('onMounted');
    });

    onUpdated(() => {
      console.log('onUpdated');
    });

    onUnmounted(() => {
      console.log('onUnmounted');
    });

    </script>

    <template>
      <div>Hello World</div>
    </template>

Svelte provides similar [APIs](https://svelte.dev/docs/svelte):

    <script>
      import { onMount, beforeUpdate, afterUpdate, onDestroy } from "svelte";

      let rand = 0;
      const random = () => {
        rand = Math.random();
      };

      console.log("Render `Lifecycle`");

      onMount(() => {
        console.log("onMount: `Lifecycle` component");
      });

      onDestroy(() => {
        console.log("onDestroy: `Lifecycle` component");
      });

      beforeUpdate(() => {
        console.log("beforeUpdate: `Lifecycle` component");
      });

      afterUpdate(() => {
        console.log("afterUpdate: `Lifecycle` component");
      });
    </script>

    <button on:click={random}>
      Svelte LifeCycle {rand}
    </button>