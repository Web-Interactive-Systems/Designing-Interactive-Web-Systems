---
type: NoteCard
tags: []
---

# Events Handling in JavaScript
Event Listener: An event listener is a function that listens for a specific event on a specific element and executes a callback when the event is triggered, such as a mouse click or a key press.

```js
const button = document.querySelector('button');

button.addEventListener('click', function() {
  console.log('Button clicked');
});
```

Event Propagation: Event propagation is the process by which events are passed from one element to another in the DOM hierarchy ("bubble up"). There are two types of event propagation: bubbling and capturing.

```js
// html
<div class="outer">
  <div class="inner">
    <button>Click me</button>
  </div>
</div>

// javascript
const outer = document.querySelector('.outer');
const inner = document.querySelector('.inner');
const button = document.querySelector('button');

outer.addEventListener('click', function() {
  console.log('Outer clicked');
});

inner.addEventListener('click', function() {
  console.log('Inner clicked');
});

button.addEventListener('click', function(event) {
  console.log('Button clicked');
  event.stopPropagation();
});

// output
```

Event Bubbling Phase: In the bubbling phase, the event is first captured by the deepest element inside the DOM hierarchy and then propagated upwards towards the outermost ancestor element. For example, if you have a button inside a div inside a section inside a main element, and you click on the button, the event will first be captured by the button, then the div, then the section, and finally the main element.

```js
// html
<div class="outer">
  <div class="inner">
    <button>Click me</button>
  </div>
</div>

// javascript
const outer = document.querySelector('.outer');
const inner = document.querySelector('.inner');
const button = document.querySelector('button');

outer.addEventListener('click', function() {
  console.log('Outer clicked');
});

inner.addEventListener('click', function() {
  console.log('Inner clicked');
});

button.addEventListener('click', function(event) {
  console.log('Button clicked');
});

// output ??
```

Event Cupturing Phase: In the capturing phase, the event is first captured by the outermost ancestor element and then propagated downwards towards the deepest element inside the DOM hierarchy. So in the previous example, the event would be first captured by the main element, then the section, then the div, and finally the button.

```js
// html
<div class="outer">
  <div class="inner">
    <button>Click me</button>
  </div>
</div>

// javascript
const outer = document.querySelector('.outer');
const inner = document.querySelector('.inner');
const button = document.querySelector('button');

outer.addEventListener('click', function() {
  console.log('Outer clicked');
} { capture: true });

inner.addEventListener('click', function() {
  console.log('Inner clicked');
});

button.addEventListener('click', function(event) {
  console.log('Button clicked');
});

// output ??
```

Event Object: An event object is an object that contains information about an event, such as the type of event, the target element, and any data associated with the event.

```js
// See `event` object in the callback 
button.addEventListener('click', function(event) {
  console.log('Button clicked');
  console.log('The event object ', event);
});

// Output ??
```

Event Delegation: Event delegation is a technique (a pattern) where an event listener is handled at a higher level (attached to a parent element), rather than to each individual child element, allowing for more efficient event handling.

```js
// html

<div id="buttons">
  <button>Button 1</button>
  <button>Button 2</button>
  <button>Button 3</button>
</div>

// js
const buttons = document.getElementById('buttons');

buttons.addEventListener('click', function(event) {
  if (event.target.tagName === 'BUTTON') {
    console.log(event.target.textContent);
  }
});

// Output
```

Event Handlers: An event handler is a function that is executed in response to a particular event being triggered. It can be attached to an element using an event listener or as an inline attribute in HTML.

```js
/// html 
<button id="add-todo">Click me</button>

// js
// This an event handler
const handleAddTodo = (event) => {
  console.log('Button clicked');
  console.log('The event object ', event);
}

const addTodoBtn = document.getElementById('add-todo');

addTodoBtn.addEventListener('click', handleAddTodo);

// Output ??
```

Event Types: There are many types of events in web development, such as mouse events, keyboard events, touch events, and form events.

```js
// Todo check MDN docs
// https://developer.mozilla.org/en-US/docs/Web/Events
```

Event Prevent Default: Some events have a default action that can be prevented. For example, clicking on a link will typically cause the browser to navigate to the link's URL. The default action can be prevented using the preventDefault() method on the event object.

```js
// html
<a href="https://www.example.com" id="myLink">Click me</a>

// js

const myLink = document.getElementById("myLink");

myLink.addEventListener("click", function(event) {
    event.preventDefault();
    console.log("Link clicked, but default behavior prevented.");
 });
```

Event Stop Propagation: We can stop events from propagating using \`stopPropagation\`.

```js
// html
<div class="outer">
  <div class="inner">
    <button>Click me</button>
  </div>
</div>

// javascript
const outer = document.querySelector('.outer');
const inner = document.querySelector('.inner');
const button = document.querySelector('button');

outer.addEventListener('click', function() {
  console.log('Outer clicked');
});

inner.addEventListener('click', function() {
  console.log('Inner clicked');
});

button.addEventListener('click', function(event) {
  console.log('Button clicked');
  event.stopPropagation();
});

// Output ??
```