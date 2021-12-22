An Observer is a consumer of values delivered by an [[Web/Javascript/RxJS/Overview#^8baff8 | Observable]]. Observers are simply a set of callbacks, one for each type of notification delivered by the Observable: `next`, `error`, and `complete`. The following is an example of a typical Observer object:

> Observers are just objects with three callbacks, one for each type of notification that an Observable may deliver.

```
const observer = {
  next: x => console.log(x),
  error: err => console.err(err),
  complete: () => console.log('completed'),
};

observable.subscribe(observer);
```

Observers might be *partial* - not all of the callbacks mentioned above have to be provided.