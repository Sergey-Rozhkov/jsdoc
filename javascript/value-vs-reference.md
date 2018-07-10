# Value vs Reference

### Объясните код

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
var a = {};

(function clear(a) {
    a.a = 10;
    a = null;
})(a);

console.log(a); // ???
```

```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};

console.log(foo.x); // ???
console.log(bar.x); // ???
```

```javascript
var obj = {
    innerObj: {foo: 9}
};
var z = obj.innerObj;
z.x = 25;
console.log(obj.innerObj.x); // ???
```

```javascript
var obj = {
    innerArr: [{x: 17}]
};
var z = obj.innerArr;
z = [{x: 25}];
console.log(obj.innerArr[0].x); // ???
```

```javascript
var obj = {
    arr: []
};
obj.arr.push(17);
console.log(obj.arr === [17]); // ???
```

```javascript
var val = (function (a) {
    arguments[0] = 10;
    return a;
})(5);
```

```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
console.log(foo); // ???
```

```javascript
var User = function () {};
User.prototype.attributes = {
    isAdmin: false
};
var admin = new User("Sam"),
    guest = new User("Bob");

admin.attributes.isAdmin = true;

console.log('admin', admin.attributes.isAdmin); // ???
console.log('guest', guest.attributes.isAdmin); // ???
```

```javascript
var obj = {
    a: 1
};

(function (obj) {
    obj = {a: 2};
})(obj);

console.log(obj.a); // ???
```

