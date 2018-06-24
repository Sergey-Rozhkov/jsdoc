# Value vs Reference

### Объясните код

```javascript
var obj = {
    innerObj: {
        x: 9
    }
};
​
var z = obj.innerObj;
​
z.x = 25;
​
console.log(obj.innerObj.x);
```

```javascript
var obj = {
    arr: [{ x: 17 }]
};
​
var z = obj.arr;
​
z = [{ x: 25 }];
​
console.log(obj.arr[0].x);
```

```javascript
var obj = {
    arr: []
};
​
obj.arr.push(17);
​
console.log(obj.arr === [17]);
```

```javascript
(function(a) {
  arguments[0] = 10;
  return a;
})(5);
```

```javascript
var foo = { n: 1 };
var bar = foo;
foo.x = foo = { n: 2 };
console.log(foo);
```

```javascript
var User = function() {};

User.prototype.attributes = {
  isAdmin: false
};

var admin = new User("Sam"),
    guest = new User("Bob");

admin.attributes.isAdmin = true;

console.log('admin', admin.attributes.isAdmin);
console.log('guest', guest.attributes.isAdmin);
```

```javascript
var obj = {
  a: 1
};

(function(obj) {
  obj = {
    a: 2
  };
})(obj);

console.log(obj.a); // ???
```

```javascript
var a = {};

(function b ( a ) {
    a.a = 10;
    a = null;
})( a );

console.log(a); // ???
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

