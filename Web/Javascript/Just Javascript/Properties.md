# Properties
Meet Sherlock Holmes, a world-renowned detective from London:

```
let sherlock = {
  surname: 'Holmes',
  address: { city: 'London' } 
};
```

His friend John Watson has recently moved in to live with Sherlock:

```
let john = {
  surname: 'Watson',
  address: sherlock.address
};
```

Sherlock is a brilliant detective but a difficult flatmate. One day, John decides he’s had enough. John changes his surname and moves to live in Malibu:

```
john.surname = 'Lennon';
john.address.city = 'Malibu';
```

Time for a small exercise. **Write down your answers to these questions:**

```
console.log(sherlock.surname); // Holmes
console.log(sherlock.address.city); // Malibu
console.log(john.surname); // Lennon
console.log(john.address.city); // Malibu
```

Both **variables** and **properties** ack like _wires_. Properties do not contain values, they point at them.