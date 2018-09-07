# Closures

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

