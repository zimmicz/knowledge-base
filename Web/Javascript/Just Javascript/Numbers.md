# Numbers
```
console.log(0.1 + 0.2 === 0.3); // false
console.log(0.1 + 0.2 === 0.30000000000000004); // true
```

Javascript is using floating point math. There are only 18 quintillion numbers available, so it always picks the closest it knows about.

Javascript treats number as having a limited precision.

![[numbers.gif]]

## Special numbers
Floating point math includes a few special numbers like `NaN`, `Infinity`, `-Infinity`.

```
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```

```
console.log(typeof(NaN)); // "number"
```