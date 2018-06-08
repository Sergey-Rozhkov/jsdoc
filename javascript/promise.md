# Promise

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
        return Promise().reject();
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

