# RxJs

{% embed data="{\"url\":\"https://www.learnrxjs.io/operators/\",\"type\":\"link\",\"title\":\"Operators · learn-rxjs\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.learnrxjs.io/gitbook/images/apple-touch-icon-precomposed-152.png\",\"width\":152,\"height\":152,\"aspectRatio\":1}}" %}

{% embed data="{\"url\":\"http://rxmarbles.com/\",\"type\":\"link\",\"title\":\"RxMarbles: Interactive diagrams of Rx Observables\",\"description\":\"Learn, build, and test Rx functions on Observables\",\"icon\":{\"type\":\"icon\",\"url\":\"http://rxmarbles.com/favicon.png\",\"aspectRatio\":0}}" %}

* Combination
  * `zip` - After all observables emit, emit values as an array.
  * `concat` - Subscribe to observables in order as previous completes, emit values.
  * `forkJoin` - When all observables complete, emit the last value from each.
  * `concatAll` - Collect observables and subscribe to next when previous completes.
* Conditional
* Creation
  * `of` - Emit variable amount of values in a sequence.
  * `from` - Turn an array, promise, or iterable into an observable.
  * `range`
  * `timer`
* Error Handling
  * `catch` - Gracefully handle errors in an observable sequence.
* Multicasting
* Filtering
  * `filter` - Emit values that pass the provided condition.
  * `debounce` - Discard emitted values that take less than the specified time
  * `debounceTime` - Discard emitted values that take less than the specified time between output
* Transformation
  * `buffer` - Collect output values until provided observable emits, emit as array.
  * `map` - Apply projection with each value from source.
  * `flatMap` is an alias for `mergeMap`!
  * `mergeMap` - Map to observable, emit values.
  * `switchMap` - Map to observable, complete previous inner observable, emit values.
  * `concatMap` - Collect observables and subscribe to next when previous completes.
  * `reduce` - Reduces the values from source observable to a single value that's emitted when the source completes.
* Utility
  * `do` - Transparently perform actions or side-effects, such as logging.
  * `toPromise` - Convert observable to promise.

