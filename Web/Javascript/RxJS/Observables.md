Observables are lazy Push collections of multiple values. They fill the missing spot in the following table:

| | Single | Multiple |
| ------ | ------ | -------- |
| Pull | Function | Iterator |
| Push | Promise | Observable |

## Pull vs Push

**What is Pull?** In Pull systems, the Consumer determines when it receives data from the data Producer. The Producer itself is unaware of when the data will be delivered to the Consumer.

Every JavaScript Function is a Pull system. The function is a Producer of data, and the code that calls the function is consuming it by "pulling" out a _single_ return value from its call.

| | Producer | Consumer |
| ------ | ------ | -------- |
| Pull | Passive: produces data when requested | Active: decides when data is requested |
| Push | Active: produces data at its own pace | Passive: reacts to receive data |

**What is Push?** In Push systems, the Producer determines when to send data to the Consumer. The Consumer is unaware of when it will receive that data.

Promises are the most common type of Push system in JavaScript today. A Promise (the Producer) delivers a resolved value to registered callbacks (the Consumers), but unlike functions, it is the Promise which is in charge of determining precisely when that value is "pushed" to the callbacks.

**Observables are a new Push system for Javascript.** An Observable is a Producer of multiple values, "pushing" them to Observers (Consumers).

-   A **Function** is a lazily evaluated computation that synchronously returns a single value on invocation.
-   A **generator** is a lazily evaluated computation that synchronously returns zero to (potentially) infinite values on iteration.
-   A **Promise** is a computation that may (or may not) eventually return a single value.
-   An **Observable** is a lazily evaluated computation that can synchronously or asynchronously return zero to (potentially) infinite values from the time it's invoked onwards.

Observables are lazy computations, until they are "called" (with `subscribe`), they won't be executed. On top of that, two Observable subscribes trigger two separate side effects.

> Subscribing to an Observable is analogous to calling a Function.

> Observables are able to deliver values either synchronously or asynchronously.

**The big difference between Observables and Functions is that Observables can return multiple values over time.**