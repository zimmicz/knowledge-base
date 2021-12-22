Service workers (SW) act as proxy servers that sit between web apps, the browser and the network. They can intercept network requests, create effective offline experiences, use background sync APIs and push notifications.

They:
- don't have access to DOM
- run on different thread than the main JS code powering the app -> nonblocking
- are designed to be fully async -> synchronous APIs can't be used

## Registration
If successful, service worker will be downloaded to the client and attempt to install/activate.

## Download, install and activate
SW is immediately downloaded when a user first accesses a SW-controlled site/page. After that, it is updated when:
- a navigation to in-scope page occurs
- an event is fired on the SW and it hasn't been downloaded in last 24 hours
