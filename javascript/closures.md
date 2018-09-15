---
description: >-
  Замыкание — это комбинация функции и лексического окружения, в котором эта
  функция была определена.
---

# Closures

{% embed data="{\"url\":\"https://developer.mozilla.org/ru/docs/Web/JavaScript/Closures\",\"type\":\"link\",\"title\":\"Замыкания\",\"description\":\"Замыкание — это комбинация функции и лексического окружения, в котором эта функция была определена.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://developer.mozilla.org/static/img/favicon144.e7e21ca263ca.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://developer.mozilla.org/static/img/opengraph-logo.72382e605ce3.png\",\"width\":600,\"height\":600,\"aspectRatio\":1}}" %}

## [Understanding JavaScript Closures](https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/)

### Объясните код

```javascript
function getClosure() {
    var canYouSeeMe = "here I am";
    return (function theClosure() {
        return {canYouSeeIt: canYouSeeMe ? "yes!" : "no"};
    });
}

var closure = getClosure();
console.log(closure().canYouSeeIt);  // ???
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

```javascript
var myVar = 'hello';

function myFunc() {
    console.log(myVar); // ???
    var myVar = 'goodbye';
    console.log(myVar); // ???
}

myFunc();
console.log(myVar); // ???
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

