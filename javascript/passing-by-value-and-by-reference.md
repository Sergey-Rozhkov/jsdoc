# Passing by value and by reference

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

console.log(obj.a);
```

```javascript
var a = {};

(function b ( a ) {
    a.a = 10;
    a = null;
})( a );

console.log(a);
```

