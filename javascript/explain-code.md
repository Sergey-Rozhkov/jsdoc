# Explain code

```javascript
var a = { b: 1 }, c = Object.create(а);

console.log(c.b); // ?
delete с.b;
сonsole.log(c.b); // ?
delete a.b;
сonsole.log(с.b); // ?
a.z = 2;
сonsole.log(с.z); // ?
с.z = 3;
сonsole.log(a.z); // ?
```

```javascript
var obj = {
  prop: 10,
  fnc: function() {
    return this.prop; 
  }
}
obj.fnc(); // ???
var fnc = obj.fnc;
fnc(); // ???
```

```javascript
var obj = {
  fnc: function(){
    console.log(this.prop);
  },
  prop: 1
};

obj.fnc.prop = 2;
obj.fnc();  //  ???
var fn = obj.fnc;
fn();       //  ???
obj.prop = 2;
obj.fnc();  //  ???
```

```javascript
let f = i => j => j ? f(i + j) : i
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
var a = 42;
var b = "foo";

a < b; // ?
a > b; // ?
a == b; // ?
```

```javascript
var a = {};

function clear(obj) {
  obj.foo = 123;
  obj = null; 
}

clear(a);
console.log(a); // ???
```

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
console.log(1);
setTimeout(function() {
  console.log(2); 
})
console.log(3);
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

```javascript
var a = {key: 'foo'};
var b = {key: 'bar'};
var c = {};

c[a] = 123; 
c[b] = 345; 
console.log(c[a], c[b]); // ???
```

```javascript
'b' + 'a' + + 'a'
```

```javascript
for (var i = 0; i < 10; i++) {
	setTimeout(function(){console.log(i)}, 100);
}
```

