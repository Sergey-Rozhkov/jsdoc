# Closures

## [Understanding JavaScript Closures](https://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/)

### Объясните код

```javascript
function getClosure() {
    var canYouSeeMe = "here I am";
    return (function theClosure() {
        return {canYouSeeIt: canYouSeeMe ? "yes!": "no"};
    });
}

var closure = getClosure();
closure().canYouSeeIt; //"yes!"
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
    console.log(myVar);
    var myVar = 0;
    console.log(myVar);
}
myFunc();
console.log(myVar);     // hello
```

