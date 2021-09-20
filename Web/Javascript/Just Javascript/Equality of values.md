# Equality of values

## Kinds of equality
* [[#Strict equality]] `a === b`
* Loose equality `a == b`
* [[#Same value equality]] `Object.is(a, b)`

### Same value equality
```
console.log(Object.is(2, 2)); // true
console.log(Object.is({}, {})); // false
```

```
let dwarves = 7;
let continents = '7';
let worldWonders = 3 + 4;
console.log(Object.is(dwarves, continents)); // false
console.log(Object.is(continents, worldWonders)); // false
console.log(Object.is(worldWonders, dwarves)); // true
```

```
let banana = {};
let cherry = banana;
let chocolate = cherry;
cherry = {};
```
1. `banana` is wired to `{}`
2. `cherry` is wired to the same `{}`
3. `chocolate` is wired to the same `{}`
4. `cherry` is wired to different `{}`

```
console.log(Object.is(banana, cherry)); // false
console.log(Object.is(cherry, chocolate)); // false
console.log(Object.is(chocolate, banana)); // true
```

### Strict equality
In almost all situtations, strict equality behaves the same way as [[#Same value equality]], but there are two exceptions to the rule:
1. `NaN === NaN` is false
2. `-0 === 0`, `0 === -0` are true

```
let width = 0 / 0; // NaN
let height = width * 2; // NaN
console.log(width === height); // false
console.log(Object.is(width, height)); // true
```

To check if number is `NaN`, use:
* `Number.isNaN(number)`
* `Object.is(number, NaN)`
* `number !== number`, because `NaN` is the only number that is not equal to itself

---
```
let width = 0; // 0
let height = -width; // -0
console.log(width === height); // true
```

However, `0` is a _different value_ from `-0`:

```
console.log(Object.is(width, height)); // false
```

### Coding exercise
**Write a function called `strictEquals(a, b)` that returns the same value as `a === b`. Your implementation must not use the `===` or `!==` operators.**

Answer is at https://gist.github.com/gaearon/08a85a33e3d08f3f2ca25fb17bd9d638?ck_subscriber_id=1182441437