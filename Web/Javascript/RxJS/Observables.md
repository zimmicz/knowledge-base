Observables are **lazy Push collections of multiple values**. They fill the missing spot in the following table:

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

## Creating Observable
```
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
	setInterval(() => {
		subscriber.next('hi');
	}, 1000);
});
```

## Subscribing to Observables
```
observable.subscribe(x => console.log(x));
```

> Subscribing to an Observable is like calling a function, providing callbacks where the data will be delivered to.

This is drastically different to event handler API using `addEventListener/removeEventListener`. With `observable.subscribe`, the given Observer is not registered as a listener in the Observable. The Observable does not even maintain a list of attached Observers.

## Executing Observables
The execution produces multiple values over time, either synchronously or asynchronously.

There are three types of values an Observable Execution can deliver:
-   "Next" notification: sends a value such as a Number, a String, an Object, etc.
-   "Error" notification: sends a JavaScript Error or exception.
-   "Complete" notification: does not send a value.

## Disposing Observable Executions
```
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
    const id = setInterval(() => {
        console.log('observable hi');
        subscriber.next('hi');
    }, 1000);

    return () => clearInterval(id);
})

const sub1 = observable.subscribe(value => {
    console.log('sub1', value);
});


const sub2 = observable.subscribe(value => {
    console.log('sub2', value);
});

sub1.unsubscribe();
sub2.unsubscribe();
```
When `observable.subscribe` is called, the [[Web/Javascript/RxJS/Overview#^3abcc2|Observer]] gets attached to the newly created Observable execution. This call also returns a [[Web/Javascript/RxJS/Overview#^7bf096|Subscription]] object.

Each observable must define how to dispose resources:
- either by using the default unsubscribe function returned from `observable.subscribe`
- or by using a custom function returned from `observable.subscribe`
