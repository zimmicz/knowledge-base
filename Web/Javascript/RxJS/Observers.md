An Observer is a consumer of values delivered by an [[Overview#^8baff8 | Observable]]. Observers are simply a set of callbacks, one for each type of notification delivered by the Observable: `next`, `error`, and `complete`. The following is an example of a typical Observer object: