Operators are functions and there are two types of them:
1. **Pipeable Operators** - when called, they do not change the existing Observable instance, they return a new Observable instead with subscription logic based on the first one
2. **Creation Operators** - can be called as a standalone function to create a new Observable