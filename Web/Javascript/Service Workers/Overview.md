Service workers act as proxy servers that sit between web apps, the browser and the network. They can intercept network requests, create effective offline experiences, use background sync APIs and push notifications.

They:
- don't have access to DOM
- run on different thread than the main JS code powering the app -> nonblocking
- are designed to be fully async -> synchronous APIs can't be used

## Registration
