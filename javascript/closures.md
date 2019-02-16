---
description: >-
  Замыкание — это комбинация функции и лексического окружения, в котором эта
  функция была определена.
---

# Closures

### Материал

{% embed url="https://developer.mozilla.org/ru/docs/Web/JavaScript/Closures" %}

{% embed url="https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/" %}

```javascript
function getConunter() {
  var counter = 0;

  return function() {
    return ++counter;
  };
}

var myCounterMans = getCounter();
var myCounterWoMans = getCounter();

myCounterMans(); // ?
myCounterMans(); // ?
myCounterWoMans(); // ?
myCounterMans(); // ?
```

```javascript
var x = "global";

function outer() {
    var y = "outer";

    function inner() {
        var x = "inner";
    }
}
```

### Объяснить код

```javascript
var myVar = 'hello';

function myFunc() {
  console.log(myVar); // ?
  var myVar = 'goodbye';
  console.log(myVar); // ?
}

myFunc();
console.log(myVar); // ?
```

```javascript
var a = 1;
var b = 2;

(function() {
  var b = 3;
  a += b;
})();

a; // ?
b; // ?
```

```javascript
function getClosure() {
    var canYouSeeMe = "here I am";
    return (function theClosure() {
        return {canYouSeeIt: canYouSeeMe ? "yes!" : "no"};
    });
}

var closure = getClosure();
console.log(closure().canYouSeeIt);  // ?
```

```javascript
function makeAdder(a) {
  return function(b) {
    return a + b;
  };
}

var x = makeAdder(5);
var y = makeAdder(20);
x(6); // ?
y(7); // ?
```

