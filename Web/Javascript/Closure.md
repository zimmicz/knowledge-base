# Closure

> In short, a "closure" occurs when a bit of "state", created inside of a function body, is exposed, with some indirection, to the outside world in the function's return. To make sense of this, let's break down a few things.

> You have a closure when **a function accesses variables defined outside of it**.

> A closure is created when state held inside of a function body is exposed to the world outside of that function through its return value. It remains accessible, albeit indirectly, so long as the returned value exists in the program.

```js
function createCounter() {
  let count = 0

  return {
    /**
     * Read the current state
     */
    state: () => count,
    /**
     * Increment the state by 1
     */
    increment: () => {
      count++
    },
    /**
     * Decrement the state by 1
     */
    decrement: () => {
      count--
    },
  }
}

const counter = createCounter()

console.log(counter.state()) // 0
counter.increment()
counter.increment()
counter.increment()
console.log(counter.state()) // 3
```

For example, this code snippet contains a closure:

```js
let users = ['Alice', 'Dan', 'Jessica'];
let query = 'A';
let user = users.filter(user => user.startsWith(query));
```

## Sources
- https://kyleshevlin.com/what-is-a-closure
- https://whatthefuck.is/closure