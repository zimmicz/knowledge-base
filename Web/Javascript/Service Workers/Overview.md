Service workers (SW) act as proxy servers that sit between web apps, the browser and the network. They can intercept network requests, create effective offline experiences, use background sync APIs and push notifications.

They:
- don't have access to DOM
- run on different thread than the main JS code powering the app -> nonblocking
- are designed to be fully async -> synchronous APIs can't be used

## Registration
If successful, service worker will be downloaded to the client and attempt to install/activate.

## Download, install and activate
SW is immediately downloaded when a user first accesses a SW-controlled site/page. After that, **it is updated when**:
- a navigation to in-scope page occurs
- an event is fired on the SW and it hasn't been downloaded in last 24 hours

**It is installed when**:
- the downloaded file is new (byte-wise compared)
- first SW encountered for this page/site

First time the SW has been made available, installation is attempted and then it is activated.

## What happens when existing SW is encountered
- new SW version is installed in the background
- **it is not activated yet** (*worker in waiting*)
- it is only activated when there are no longer any pages loaded still using the old SW
- activation can happen sooner and existing pages can be claimed by the active worker