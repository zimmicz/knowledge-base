# [[Web/Javascript/Just Javascript/Basics#Primitive values|Values]] and variables

```
let reaction = 'yikes';
reaction[0] = 'l';
console.log(reaction);
```

This will print **yikes**, because **primitive values are immutable**.

![[values_variables.png]]

```
let pet = 'Narwhal';
pet = 'The Kraken';
console.log(pet); // ?
```
This will print **The Kraken**, because the value is not being modified, rather the variable leads to a different value.

## Variables are wires
It is not that **Narwhal** was changing into **The Kraken**, it is `pet` is changing the value it leads to.

**Variables are not values. Variables point to values.**

A variable is a wire between between the name and the value it represents.

![[variables.gif]]

![[variables_2.gif]]

The left side of an assignment must be a wire. The right side of an assignment must be an [[Web/Javascript/Just Javascript/Basics#Expressions|expression]].

`The Kraken` or `2` are also expressions, but they are called literals - because we literally write down their values.

## Reading a value of a variable

```
console.log(pet);
```
The value of a variable can also be read. But it is not the `pet` variable that is passed to a function, it is its **value**.

```
function double(x) {
  x = x * 2;
}

let money = 10;
double(money);
console.log(money); // 10
```
If variable `money` was passed to `double`, it would lead to `money` being doubled to `20`. Since only the value represented by the `money` variable is sent, `money` is still `10` afterwards.

**Only values are passed to functions, not variables**.

## Example
```
let x = 10;
let y = x;
x = 0;
```

1. variable `x` is wired to value `10`
2. variable `y` is wired to value of variable `x`, that is `10` again
3. variable `x` is wired to value `0`
4. `x ===0; y === 10`

**Variables always point at values.**