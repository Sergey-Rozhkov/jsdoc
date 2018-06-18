# Hoisting and types

### Объясните код

{% code-tabs %}
{% code-tabs-item title="function" %}
```javascript
function foo() {
    var x;
    function x() {}
    console.log(typeof x);
};
foo(); // ???
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="number" %}
```javascript
function foo() {
    var x;
    function x() {}
    x = 1;
    console.log(typeof x);
};
foo(); // ???
```
{% endcode-tabs-item %}
{% endcode-tabs %}

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
var x = 1; 
console.log(x); // ??? 
if (true) { 
    var x = 2; 
    console.log(x); // ???
} 
console.log(x); // ???
```

```javascript
var a = 1;

function foo() {
	console.log(a);
}

function bar() {
    var a = 2;
    foo();
}

bar(); // ???
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
test(); // ???
```

