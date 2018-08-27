# Promise

Объект **`Promise`** \(обещание\) используется для отложенных и асинхронных вычислений. `Promise` может находиться в трёх состояниях:

* _ожидание \(**pending**\)_: начальное состояние, не выполнено и не отклонено.
* _выполнено \(**fulfilled**\)_: операция завершена успешно.
* _отклонено \(**rejected**\)_: операция завершена с ошибкой.
* _заданный \(**settled**\)_: обещание выполнено или отклонено, но не находится в состоянии ожидания.

![](../.gitbook/assets/image%20%2833%29.png)

* [`Promise.all(iterable)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)Возвращает обещание, которое выполнится после выполнения всех обещаний в передаваемом итерируемом аргументе.
* [`Promise.race(iterable)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)Возвращает обещание, которое будет выполнено или отклонено с результатом исполнения первого выполненного или отклонённого итерируемого обещания.
* [`Promise.reject(reason)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject)Возвращает объект `Promise`, который отклонён с указанной причиной.
* [`Promise.resolve(value)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)Возвращает объект `Promise`, который выполнен с указанным значением. Если значение может быть продолжено \(имеется метод `then`\), то возвращаемое обещание будет "следовать" продолжению, выступая адаптером его состояния; в противном случае будет возвращено ожидание в выполненном состоянии.

```javascript
new Promise(executor);
new Promise(function(resolve, reject) { /* ... */ });
```

### Объясните код

```javascript
Promise.resolve(Promise.reject()).then(
  ifResolved => console.log('yes', ifResolved),
  ifRejected => console.log('no', ifRejected),
);
```

```javascript
var thenable = { then: function(resolve) {
  resolve("Resolving");
  console.log("Logging");
  throw new TypeError("Throwing");
}};

var p3 = Promise.resolve(thenable);
p3.then(function(v) {
  console.log('then', v);
}, function(e) {
  console.log('catch', v);
});
```

```javascript
Promise.reject('a')
  .catch(p => p + 'b')
  .catch(p => p + 'c')
  .then(p => p + 'd')
  .finally(p => p + 'e')
  .then(p => console.log(p));
  
console.log('f');
```

```javascript
Promise.resolve('BatMan')
    .then(function (val) {
        console.log('then', val);
        throw new Error('Error happen');
        return 'OMG!';
    })
    .then((val) => console.log('then', val))
    .catch((val) => {
        console.log('catch', val);
        return Promise.reject();
    })
    .then(firstHandler, secondHandler)
    .then(firstHandler, secondHandler)
    .then(firstHandler, secondHandler);

function firstHandler(val) {
    console.log('first', val);
}

function secondHandler(val) {
    console.log('second', val);
}
```

```javascript
Promise.reject('start')
    .finally(val => {
        console.log('finally-1', val);
        return 'one';
    })
    .catch(val => {
        console.log('catch-2', val);
        return 'two';
    })
    .finally(val => {
        console.log('finally-3', val);
        return 'three';
    })
    .then(val => {
        console.log('then-4', val);
        return 'four';
    })
    .finally(val => {
        console.log('finally-5', val);
        return 'five';
    })
    .then(val => console.log('result', val));

console.log('finish');
```

{% code-tabs %}
{% code-tabs-item title="Функция promiseTimeout" %}
```javascript
function promiseTimeout(value, timer) {
  var cb = function (resolve, reject) {
    setTimeout(() => {
      resolve(value);
    }, timer);
  };

  return new Promise(cb);
}

promiseTimeout('TWO', 2000).then(data => console.log(data));
promiseTimeout('ONE', 1000).then(data => console.log(data));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

