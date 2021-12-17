 RxJS is a library for composing asynchronous and event-based programs by using observable sequences.
 
 There is one core type - Observable - and satellite types (Observer, Schedulers, Subjects) and array like operators.
 
 > Think of RxJS as Lodash for events

ReactiveX combines
- observer pattern
- iterator pattern
- functional programming with collections

## Essential concepts

-   **[[Observables|Observable]]:** represents the idea of an invokable collection of future values or events. ^8baff8
-   **Observer:** is a collection of callbacks that knows how to listen to values delivered by the Observable. ^3abcc2
-   **Subscription:** represents the execution of an Observable, is primarily useful for cancelling the execution. ^7bf096
-   **Operators:** are pure functions that enable a functional programming style of dealing with collections with operations like `map`, `filter`, `concat`, `reduce`, etc.
-   **Subject:** is equivalent to an EventEmitter, and the only way of multicasting a value or event to multiple Observers.
-   **Schedulers:** are centralized dispatchers to control concurrency, allowing us to coordinate when computation happens on e.g. `setTimeout` or `requestAnimationFrame` or others.