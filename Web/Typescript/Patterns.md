## Branded types

```
declare const brand: unique symbol;

type Brand<T, TBrand extends string> = T & { [brand]: TBrand };

type Password = Brand<string, ‘Password’>;
const takesInPassword = (password: Password) => {}
```