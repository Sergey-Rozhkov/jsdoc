# Value vs Reference

### Объяснить код

```javascript
var a = {};

function clear(a) {
  a.a = 10;
  a = null;
}

clear(a);

console.log(a); // ?
```

```javascript
var a = {};

(function(a) {
  a.a = 10;
  a = null;
})(a);

console.log(a); // ?
```

```javascript
var a = {a: 1};

(function clear(a) {
  a.a = 2;
  a = {a: 3};
})(a);

console.log(a); // ?
```

```javascript
function makeJohnFromAlex(obj) {
    obj.name = 'john';
    return obj;
}

const alex = {
    name: 'Alex',
    age: 30,
};

const john = makeJohnFromAlex(alex);

console.log(alex); // ?
console.log(john); // ?
console.log(alex === john); // ?
```

```javascript
var a = {};
var b = a;

function clear(c) {
  c = 1;
  c.foo = null;
};

clear(b);

console.log(a, b); // ?
```

```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};

console.log(foo.x); // ?
console.log(bar.x); // ?
```

```javascript
var x = {
    innerObj: {foo: 'bar'}
};
var y = x.innerObj;
y.foo = 'baz';
console.log(obj.innerObj.foo); // ?
```

```javascript
var obj = {
    arr: [{a: 1}]
};
var x = obj.arr;
x = [{a: 2}];
console.log(obj.arr[0].a); // ?
```

```javascript
var obj = {
    arr: []
};
obj.arr.push(17);
console.log(obj.arr === [17]); // ?
```

```javascript
var val = (function (a) {
    a = 'maybe';
    arguments[0] = 'no';
    return a;
})('yes');
console.log(val); // ?
```

```javascript
var User = function () {};
User.prototype.attributes = {
    isAdmin: false
};
var admin = new User("Sam"),
    guest = new User("Bob");

admin.attributes.isAdmin = true;

console.log('admin', admin.attributes.isAdmin); // ?
console.log('guest', guest.attributes.isAdmin); // ?
```

