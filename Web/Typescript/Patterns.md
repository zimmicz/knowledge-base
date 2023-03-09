## Branded types

```typescript
declare const brand: unique symbol;

type Brand<T, TBrand extends string> = T & { [brand]: TBrand };

type Password = Brand<string, ‘Password’>;
const takesInPassword = (password: Password) => {}
const isValidPassword = (password: string): password is Password => password.length > 8;

takesInPassword('x')
// ^^^ Argument of type 'string' is not assignable to parameter of type 'Password'. Type 'string' is not assignable to type '{ [brand]: "Password"; }'.(2345)


```