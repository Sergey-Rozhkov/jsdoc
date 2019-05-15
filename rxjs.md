# RxJs

{% embed url="https://www.learnrxjs.io/operators/" %}

{% embed url="http://rxmarbles.com/" %}

{% embed url="https://blog.angularindepth.com/learn-to-combine-rxjs-sequences-with-super-intuitive-interactive-diagrams-20fce8e6511" %}



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

### Maps

* With `mergeMap` \(which has `flatMap` as an alias\), received observables are subscribed to concurrently and their emitted values are flattened into the output stream.
* With `concatMap`, received observables are queued and are subscribed to one after the other, as each completes. \(`concatMap` is `mergeMap` with a concurrency of one.\)
* With `switchMap`, when an observable is received it's subscribed to and any subscription to a previously received observable is unsubscribed.
* With `exhaustMap`, when an observable is received it's subscribed to unless there is a subscription to a previously received observable and that observable has not yet completed - in which case the received observable is ignored.

The `concatAll`, `exhaust`, `mergeAll` and `switchAll` operators for higher-order observables are implemented using the `*Map` operators.

Basically, I view `mergeMap` as being the most fundamental of the flattening operators and unless there's a compelling reason to use one of the others, I go with `mergeMap`.

In this case, the promise is only going to resolve once and there is only going to be a single observable emitted from the higher-order observable. So `concatAll`, `exhaust` and `switchAll` are redundant. The effected behaviour will be identical to that with `mergeAll`, they just involve functionality that will never be required in this instance.

### Subjects

{% embed url="https://medium.com/@luukgruijs/understanding-rxjs-behaviorsubject-replaysubject-and-asyncsubject-8cc061f1cfc0" %}

* **BehaviorSubject** имеет свойство хранить текущее значение. Это означает, что вы всегда можете напрямую получить последнее переданное значение из объекта BehaviorSubject. Можно создавать BehaviorSubjects с начальным значением.
  * `new Rx.BehaviorSubject(Math.random());`
* **ReplaySubject** сравним с BehaviorSubject тем, что он может отправлять «старые» значения новым подписчикам. Однако он обладает дополнительной характеристикой, заключающейся в том, что он может записывать часть наблюдаемого выполнения и, следовательно, сохранять несколько старых значений и «воспроизводить» их новым подписчикам. Также можно указать, как долго необходимо хранить значения.
  * `new Rx.ReplaySubject(2, 100);`
* **AsyncSubject** представляет собой вариант Subject, в котором подписчикам отправляется только последнее значение наблюдаемого выполнения, и только после завершения выполнения

### Hot vs Cold observable

{% embed url="https://blog.thoughtram.io/angular/2016/06/16/cold-vs-hot-observables.html" %}

> When the data is produced by the Observable itself, we call it a cold Observable. When the data is produced outside the Observable, we call it a hot Observable.

Observable, будучи просто функцией, может быть как «горячим», так и «холодным».

{% code-tabs %}
{% code-tabs-item title="Cold Observables" %}
```javascript
import * as Rx from "rxjs";

const observable = Rx.Observable.create((observer) => {
    observer.next(Math.random());
});

// subscription 1
observable.subscribe((data) => {
  console.log(data); // 0.24957144215097515 (random number)
});

// subscription 2
observable.subscribe((data) => {
   console.log(data); // 0.004617340049055896 (random number)
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Hot Observables" %}
```javascript
import * as Rx from "rxjs";

const observable = Rx.Observable.fromEvent(document, 'click');

// subscription 1
observable.subscribe((event) => {
  console.log(event.clientX); // x position of click
});

// subscription 2
observable.subscribe((event) => {
   console.log(event.clientY); // y position of click
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Code

