# Hoisting

### Материалы

{% embed url="https://scotch.io/tutorials/understanding-hoisting-in-javascrip" caption="Understanding Hoisting in JavaScript" %}

{% embed url="https://developer.mozilla.org/en-US/docs/Glossary/Hoisting" %}

### Объяснить код

{% code-tabs %}
{% code-tabs-item title="number" %}
```javascript
function foo() {
    function x() {}
    var x = 1;
    return typeof x;
};
foo(); // ?
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="number" %}
```javascript
function foo() {
    var x = 1;
    return typeof x;
    function x() {}    
};
foo(); // ?
```
{% endcode-tabs-item %}
{% endcode-tabs %}

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
var x = 1; 
console.log(x); // ?
if (true) { 
    var x = 2; 
    console.log(x); // ?
} 
console.log(x); // ?
```

{% code-tabs %}
{% code-tabs-item title="shadowing" %}
```javascript
const f = (coll) => {
    const iter = (item, coll) => {
        // using coll
    }
    // ...
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

```javascript
var a = 1;

function foo() {
	console.log(a);
}

function bar() {
    var a = 2;
    foo();
}

bar(); // ?
```

```javascript
function test() { 
    foo();
    bar();
    var foo = function () {
        alert("FOO"); 
    } 
    function bar() {
        alert("BAR"); 
    } 
} 
test(); // ?
```

