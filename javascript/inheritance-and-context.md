# Inheritance and context

### [Наследование и цепочка прототипов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

Наследование – это создание новых «классов» на основе существующих.

* Псевдо-классовый или Декларотивный
  * ChildClass extends ParrentClass
* [Функциональный](https://learn.javascript.ru/functional-inheritance)
  * ParrentClass.call\(this, params\);
* Прототипный
  * ChildClass.prototype = ParrentClass

{% code-tabs %}
{% code-tabs-item title="Прототипное наследование" %}
```javascript
function SuperCar(){
    this.wave = 'ding';
}
SuperCar.prototype.makeSound = function(){ console.log(this.wave); };

function Car(color) {
    this.color = color;
}

// Car.prototype = Object.create(SuperCar.prototype);
Car.prototype = new SuperCar();
Car.prototype.sayYes = function(){ console.log("Yes!"); };

var obj = new Car('red');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Функциональное наследование" %}
```javascript
function SuperCar(){
    this.wave = 'beep';
    this.makeSound = function(){
        console.log(wave);
    }
}

function Car(color) {
    SuperCar.apply(this, arguments);
    this.color = color;
}

var obj = new Car('red');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="ECMAScript 6" %}
```javascript
class Rectangle extends Shape {
    constructor (id, x, y, width, height) {
        super(id, x, y);
        this.width  = width;
        this.height = height;
    }
}
class Circle extends Shape {
    constructor (id, x, y, radius) {
        super(id, x, y);
        this.radius = radius;
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="ECMAScript 5" %}
```javascript
var Rectangle = function (id, x, y, width, height) {
    Shape.call(this, id, x, y);
    this.width  = width;
    this.height = height;
};
Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle;
var Circle = function (id, x, y, radius) {
    Shape.call(this, id, x, y);
    this.radius = radius;
};
Circle.prototype = Object.create(Shape.prototype);
Circle.prototype.constructor = Circle;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Explain the difference" %}
```javascript
function User(name) {
  this.name = name;
  this.hello = function() {
    alert(this.name);
  }
}
// -- vs -- ( what is the difference ?)
function User(name) {
  this.name = name;
}
User.prototype.hello = function() {
  alert(this.name);
};
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Explain the difference" %}
```javascript
function Role(role) {
  var role = role;
  function sayRole(){
    console.log('Role: ' + role);
  }
}
// -- vs -- ( what is the difference ?)
function User(name) {
  this.name = name;
  this.sayName = function() {
    console.log('Name: ' + this.name);
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Функции привязки контекста

* `call` - вызывает функцию с указанным значением this и индивидуально предоставленными аргументами.
* `apply` - вызывает функцию с указанным значением this и аргументами, предоставленными в виде массива \(либо массивоподобного объекта\).
* `bind` - создаёт новую функцию, которая при вызове устанавливает в качестве контекста выполнения this предоставленное значение. В метод также передаётся набор аргументов, которые будут установлены перед переданными в привязанную функцию аргументами при её вызове.

{% code-tabs %}
{% code-tabs-item title="bind polyfill" %}
```javascript
Function.prototype.myBind = function(context) 
  var func = this;
  var args = Array.prototype.slice.call(arguments, 1);
  return function() {
    return func.apply(context, args.concat(arguments));
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="bind polyfill" %}
```javascript
Function.prototype.myBind = function (context, ...args1) {
  return (...args2) => this.apply(context, args2.concat(args1));
};
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="bind polyfill" %}
```javascript
function bind(func, context /*, args*/) {
  var bindArgs = [].slice.call(arguments, 2); // (1)
  function wrapper() {                        // (2)
    var args = [].slice.call(arguments);
    var unshiftArgs = bindArgs.concat(args);  // (3)
    return func.apply(context, unshiftArgs);  // (4)
  }
  return wrapper;
}

bind(mul, null, 2)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Карринг

`Каррирование` или `карринг` \(англ. currying\) в информатике — преобразование функции от многих аргументов в набор функций, каждая из которых является функцией от одного аргумента.

```javascript
function mul(a, b) {
  return a * b;
};

var double = mul.bind(null, 2); // контекст фиксируем null, он не используется

alert( double(3) ); // = mul(2, 3) = 6
alert( double(4) ); // = mul(2, 4) = 8
alert( double(5) ); // = mul(2, 5) = 10
```

### Объясните код

```javascript
var a = {b: 1},
    c = Object.create(a);

console.log(c.b); // ?
delete c.b;
console.log(c.b); // ?
delete a.b;
console.log(c.b); // ?
a.z = 2;
console.log(c.z); // ?
c.z = 3;
console.log(a.z); // ?
```

```javascript
var obj = {
    prop: 10,
    fnc: function () {
        return this.prop;
    }
}
obj.fnc();  // ???
var fnc = obj.fnc;
fnc();      // ???
```

```javascript
var obj = {
    prop: 1,
    fnc: function () {
        console.log(this.prop);
    }
};
obj.fnc.prop = 2;
obj.fnc();  //  ???
var fn = obj.fnc;
fn();       //  ???
obj.prop = 2;
obj.fnc();  //  ???
```

```javascript
for (var i = 0; i < 10; i++) {
    setTimeout(function () {
        console.log(i)
    }, 100);
}
```

