---
description: Модель событийного цикла
---

# Event loop

{% embed url="https://youtu.be/8cV4ZvHXQL4" %}

{% embed url="https://developer.mozilla.org/ru/docs/Web/JavaScript/EventLoop" %}

{% embed url="https://youtu.be/j4_9BZezSUA" %}

{% embed url="https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/" %}

### Объясните код

```javascript
console.log(1);
setTimeout(function() {
  console.log(2);
})
console.log(3);
```

```javascript
console.log('log one');
setTimeout(() => console.log('timeout'));
Promise.resolve().then(() => console.log('promise'));
console.log('log two');
```

```javascript
console.log(1);
setTimeout(() => console.log(2), 1000);
setTimeout(() => console.log(3), 0);
Promise.resolve(true).then(() => console.log(4));
setImmediate(() => console.log(5));
console.log(6);
```

```javascript
(function () {
    console.log(1);
    setTimeout(() => console.log(2), 1000);
    setTimeout(() => console.log(3), 0);
    Promise.resolve(true).then(() => console.log(4));
    setImmediate(() => console.log(5));
    console.log(6);
})();
```

```javascript
'use strict';

const fs = require(`fs`);

const TIMEOUT = 1000;

console.log(`[0]`);

setTimeout(() => console.log(`[1] setTimeout ${TIMEOUT}`), TIMEOUT);

setTimeout(() => console.log(`[2] setTimeout 0`), 0);

setImmediate(() => console.log(`[3] setImmediate`));

process.nextTick(() => console.log(`[4] process.nextTick`));

fs.readFileSync(__filename);
console.log(`[5]`);

fs.readFile(__filename, () => console.log(`[6] readFile`));

new Promise((resolve) => resolve(`[7] Promise`))
  .then(console.log);

console.log(`[8]`);
```

```javascript
console.log('script start');

setTimeout(() => console.log('setTimeout 1000'), 1000);

Promise.resolve()
    .then(() => console.log('promise one'))
    .then(() => console.log('promise two'));
    
setTimeout(() => console.log('setTimeout 0'), 0);

console.log('script end');
```

```javascript
Promise.resolve().then(() => console.log('Promise.then'));

setImmediate(() => {
    console.log('setImmediate');
    setTimeout(() => console.log('setImmediate setTimeout'), 0);
    setImmediate(() => console.log('setImmediate setImmediate'));
});

process.nextTick(() => console.log('process.nextTick'));

setTimeout(() => console.log('setTimeout'), 0);

console.log(`startup`);
```

{% embed url="https://twitter.com/i/status/855824609299636230" %}

