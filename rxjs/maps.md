# Maps

* With `mergeMap` \(which has `flatMap` as an alias\), received observables are subscribed to concurrently and their emitted values are flattened into the output stream.
* With `concatMap`, received observables are queued and are subscribed to one after the other, as each completes. \(`concatMap` is `mergeMap` with a concurrency of one.\)
* With `switchMap`, when an observable is received it's subscribed to and any subscription to a previously received observable is unsubscribed.
* With `exhaustMap`, when an observable is received it's subscribed to unless there is a subscription to a previously received observable and that observable has not yet completed - in which case the received observable is ignored.

The `concatAll`, `exhaust`, `mergeAll` and `switchAll` operators for higher-order observables are implemented using the `*Map` operators.

Basically, I view `mergeMap` as being the most fundamental of the flattening operators and unless there's a compelling reason to use one of the others, I go with `mergeMap`.

In this case, the promise is only going to resolve once and there is only going to be a single observable emitted from the higher-order observable. So `concatAll`, `exhaust` and `switchAll` are redundant. The effected behaviour will be identical to that with `mergeAll`, they just involve functionality that will never be required in this instance.

