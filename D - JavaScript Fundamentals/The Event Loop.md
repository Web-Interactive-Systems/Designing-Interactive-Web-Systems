---
type: NoteCard
tags: []
---

# The Event Loop
JavaScript uses an event-driven, non-blocking I/O model for managing the order in which code is executed in a program, as well as handling asynchronous operations such as user input, network requests, and timers. This model is called: “The event loop”.

```js
function first() {
  console.log('Hello from first');
}

function second() {
  console.log('Hello from second');
}

first();
second();
```

::::cal
We define two functions, first and second. We then call first and second in a sequence. When we run this code, the event loop starts by executing first, which logs "Hello from first" to the console. Once first is finished executing, the event loop moves on to execute second, which logs "Hello from second" to the console.

::::

```js
function first() {
  console.log('Hello from first');
}

function second() {
  console.log('Hello from second');
}

setTimeout(first, 2000);
second();

// Output ??
```

::::cal
We define two functions, the first and second. We call first immediately using the setTimeout function to schedule the execution after a delay of 2000 milliseconds (2 seconds). Next, we call second. When we run this code, the event loop starts by executing setTimeout(first, 2000) which schedules the execution of first to occur in 2 seconds. The event loop then moves on to the next task, which is to call second. Once the delay is over, the event loop moves on to execute first.

::::

```js
function first() {
  console.log('Hello from first');
}

function second() {
  console.log('Hello from second');
  setTimeout(third, 2000);
}

function third() {
  console.log('Hello from third');
}

first();
setTimeout(second, 2000);

// Output ??
```

::::cal
**Todo**:

Explain the event loop for this example.

::::

```js
let count = 0;

function incrementCount() {
  count++;
  console.log('Count:', count);
}

setInterval(incrementCount, 1000);
```

::::cal
We define a variable count and a function incrementCount that increments the value of count and logs it to the console. We then use the setInterval function to schedule the execution of incrementCount every 1000 milliseconds (1 second).

::::