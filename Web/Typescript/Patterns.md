## Branded types

```typescript
declare const brand: unique symbol;

type Brand<T, TBrand extends string> = T & { [brand]: TBrand };

type Password = Brand<string, ‘Password’>;
const takesInPassword = (password: Password) => {}
const isValidPassword = (password: string): password is Password => password.length > 8;

const password = '12345678';

if (isValidPassword(password)) {
  takesInPassword(invalidPassword)
}
```

## Globals

```typescript
declare global { function myFunc(): boolean; var myVar: number; }
console.log(myVar); console.log(myFunc());
```

## Assertion functions and type predicates

```typescript
const values = ["a", "b", undefined, "c", undefined];
const filteredValues = values.filter((value): value is string => Boolean(value), );
```

## Classes
```typescript
export class SDK {
  loggedInUser?: User;

  constructor(loggedInUser?: User) {
    this.loggedInUser = loggedInUser;
  }

  assertIsLoggedIn(): asserts this is this & { loggedInUser: User } {
    if (!this.loggedInUser) {
      throw new Error("Not logged in");
    }
  }
}
```