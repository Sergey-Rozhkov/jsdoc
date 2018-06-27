# Types conversion

```javascript
var a = {key: 'foo'};
var b = {key: 'bar'};
var c = {};

c[a] = 123; 
c[b] = 345; 
console.log(c[a], c[b]); // ???
```

```javascript
var a = 42;
var b = "foo";

a < b; // ?
a > b; // ?
a == b; // ?
```

```javascript
const bool = new Boolean(false);
if (bool) console.log(bool);
if (bool == false) console.log(bool);
```

```javascript
true + false
12 / "6"
"number" + 15 + 3
15 + 3 + "number"
[1] > null
"foo" + + "bar"
'true' == true
false == 'false'
null == ''
!!"false" == !!"true"
[‘x’] == ‘x’
[] + null + 1
[1,2,3] == [1,2,3]
{}+[]+{}+[1]
!+[]+[]+![]
new Date(0) - 0
new Date(0) + 0
'b' + 'a' + + 'a'
1 + '1' - '1'
1 > 2 > 3
3 < 2 < 1
```

```javascript
function MyObj(val){
  this.val = val;
  this.valueOf = function () {
    console.log('valueOf', this.val);
    return this.val.valueOf();
  };
  this.toString = function () {
    console.log('toString', this.val);
    return this.val.toString();
  };
}

var a = new MyObj(1);
var b = new MyObj('2');

console.log(a > b);
console.log(a + b);
console.log(a, b);
```

