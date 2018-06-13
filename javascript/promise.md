# Promise

Объект **`Promise`** \(обещание\) используется для отложенных и асинхронных вычислений. `Promise` может находиться в трёх состояниях:

* _ожидание \(pending\)_: начальное состояние, не выполнено и не отклонено.
* _выполнено \(fulfilled\)_: операция завершена успешно.
* _отклонено \(rejected\)_: операция завершена с ошибкой.

Другой термин, описывающий состояние _заданный \(settled\)_: обещание выполнено или отклонено, но не находится в состоянии ожидания.

![](../.gitbook/assets/image%20%2831%29.png)

* [`Promise.all(iterable)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)Возвращает обещание, которое выполнится после выполнения всех обещаний в передаваемом итерируемом аргументе.
* [`Promise.race(iterable)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)Возвращает обещание, которое будет выполнено или отклонено с результатом исполнения первого выполненного или отклонённого итерируемого обещания.
* [`Promise.reject(reason)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject)Возвращает объект `Promise`, который отклонён с указанной причиной.
* [`Promise.resolve(value)`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)Возвращает объект `Promise`, который выполнен с указанным значением. Если значение может быть продолжено \(имеется метод `then`\), то возвращаемое обещание будет "следовать" продолжению, выступая адаптером его состояния; в противном случае будет возвращено ожидание в выполненном состоянии.

```javascript
new Promise(executor);
new Promise(function(resolve, reject) { ... });
```

```javascript
var bluebird = require('bluebird');

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
        console.log(val);
        throw new Error();
    })
    .then((val) => console.log('then', val))
    .catch((val) => {
        console.log('catch', val);
        return Promise.reject();
    })
    .then(firstHandler, secondHandler)
    .then(firstHandler, secondHandler)
    .then(firstHandler, secondHandler);

function firstHandler() {
    console.log('first');
}

function secondHandler() {
    console.log('second');
}
```

