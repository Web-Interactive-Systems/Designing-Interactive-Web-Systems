---
type: NoteCard
tags: []
---

# Understanding React Data Binding, Rendering, View State
Data binding is the way to keep the state of the application synchronized with the view (what is displayed in the real DOM). Whenever there is a change in the state, the view gets updated automatically.

There are two types of data binding in React: One-way data binding and Two-way data binding.

## One-way data binding

In one-way data binding, the data flows in a single direction, from the state to the view. Any changes made to the state will update the view.

```js
function ParentComponent() {
  const [name, setName] = useState('World');

  return (
    <div>
      <h2>Parent Component</h2>
      <p>Name: {name}</p>
      <ChildComponent name={name} />
    </div>
  );
}

function ChildComponent(props) {
  return (
    <div>
      <h2>Child Component</h2>
      <p>Name: {props.name}</p>
    </div>
  );
}
```

*   In this example, the parent component ParentComponent has a state variable name which is initially set to 'Worl'.
*   This variable name is passed as a prop to the child component ChildComponent.
*   When the parent component updates the name variable using the setName function, the child component receives the updated name prop and re-renders accordingly.

## Two-way data binding

In two-way data binding, the data flows in both directions, from the state to the view and from the view to the state. Any changes made to the state or the view will update the other.

```js
function ParentComponent() {
  const [name, setName] = useState('John');

  function handleChange(event) {
    setName(event.target.value);
  }

  return (
    <div>
      <h2>Parent Component</h2>
      <p>Name: {name}</p>
      <ChildComponent name={name} onChange={handleChange} />
    </div>
  );
}

function ChildComponent(props) {
  return (
    <div>
      <h2>Child Component</h2>
      <input type="text" value={props.name} onChange={props.onChange} />
    </div>
  );
}
```