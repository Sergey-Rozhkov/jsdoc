---
description: >-
  When the data is produced by the Observable itself, we call it a cold
  Observable. When the data is produced outside the Observable, we call it a hot
  Observable.
---

# Hot vs Cold observable

{% embed url="https://blog.thoughtram.io/angular/2016/06/16/cold-vs-hot-observables.html" %}

Observable, будучи просто функцией, может быть как «горячим», так и «холодным».

{% code title="Cold Observables" %}
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
{% endcode %}

{% code title="Hot Observables" %}
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
{% endcode %}

