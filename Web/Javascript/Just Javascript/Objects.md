# Objects
This includes arrays, dates, RegExps, and other non-primitive values:

```
console.log(typeof({})); // "object"
console.log(typeof([])); // "object"
console.log(typeof(new Date())); // "object"
console.log(typeof(/\d+/)); // "object"
console.log(typeof(Math)); // "object"
```

**Objects are not primitive values. They are mutable.**

```
let rapper = { name: 'Malicious' };
rapper.name = 'Malice'; // Dot notation
rapper['name'] = 'No Malice'; // Bracket notation
```

We can make more of them, we can create our own objects.

Every time `{}` is used, a new object value is created.

```
let shrek = {};
let donkey = {};
```

![[objects.png]]

Javascript is garbage-collected language, objects are destroyed once they become unreachable by following wires from our code.