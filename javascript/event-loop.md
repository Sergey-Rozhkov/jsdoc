---
description: Модель событийного цикла
---

# Event loop

{% embed url="https://youtu.be/8cV4ZvHXQL4" %}

{% embed url="https://developer.mozilla.org/ru/docs/Web/JavaScript/EventLoop" %}

{% embed url="https://youtu.be/j4\_9BZezSUA" %}

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
console.log(5);
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
console.log('script start');
setTimeout(function () {
    console.log('setTimeout 1000');
}, 1000);
Promise.resolve()
    .then(function () {
        console.log('promise one');
    })
    .then(function () {
        console.log('promise two');
    });
setTimeout(function () {
    console.log('setTimeout 0');
}, 0);    
console.log('script end');
```



