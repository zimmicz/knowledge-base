# Mutations
**[[Objects]] might appear “nested” in code, but in our universe each object is completely separate. An object cannot be “inside” of other object!**

![[mutations.gif]]

_Mutation_ is a fancy way of saying “change”.

**By mutating an object used elsewhere in the program, we’ve made a mess.**

See [[Properties]] for the code being used.

## Mutating another object
```
// Replace Step 3 with this code:
john.surname = 'Lennon';
john.address = { city: 'Malibu' };
```

![[mutations.png]]

## No object mutation
```
// Replace Step 3 with this code:
john = {
  surname: 'Lennon',
  address: { city: 'Malibu' }
};
```

![[mutations_2.png]]

**By the time you mutate an object, variables and properties may already be pointing at it. Your mutation affects any code “following” those wires later.**