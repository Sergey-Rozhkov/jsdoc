# Inheritance and context

### [Наследование и цепочка прототипов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

Наследование – это создание новых «классов» на основе существующих.

> **Objects** does not have _prototype_ property. It has _\_\_proto\_\__ property.

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
{% code-tabs-item title="Inheritance" %}
```javascript
function Animal(name) {
  this.name = name;
  this.jump = function() {
    console.log(this.name + ' jump');
  };
}

Animal.prototype.run = function() {
  console.log(this.name + ' run');
};

function Cat(catType) {
  this.type = catType;

  Animal.apply(this, Array.prototype.slice.call(arguments, 1));
}

Cat.prototype = Object.create(Animal.prototype);
Cat.prototype.constructor = Cat;

Cat.prototype.voice = function() {
  console.log('meow');
};

let cat = new Cat('British', 'Alex');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

```javascript
function A() {
    this.propA = 'A';
    this.sayA = function() {
        console.log(this.propA);
    };
}

A.prototype.funcA = function() {
    console.log('funcA');
};

function B() {
    A.call(this);
    this.propB = 'B';
    this.sayB = function() {
        console.log(this.propB);
    };
}

B.prototype = Object.create(A.prototype);
B.prototype.constructor = B;

B.prototype.funcB = function() {
    console.log('funcB');
};

////////////////////////////////////////////////////////////////////////////////

var a = new A();
var b = new B();

console.log('a.propA', a.propA);
console.log('b.propB', b.propB);
```

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

* `call` - вызывает функцию с указанным значением **this** и индивидуально предоставленными аргументами.
* `apply` - вызывает функцию с указанным значением **this** и аргументами, предоставленными в виде массива \(либо массивоподобного объекта\).
* `bind` - создаёт новую функцию, которая при вызове устанавливает в качестве контекста выполнения **this** предоставленное значение. В метод также передаётся набор аргументов, которые будут установлены перед переданными в привязанную функцию аргументами при её вызове.

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

```javascript
functiob sum(a, b, c, d) {
  return a + b + c + d;
}

const sum3 = sum.bind(null, 1, 2, 3);

sum2(3) // 9
sum2(10) // 16
```

### Карринг

`Каррирование` или `карринг` \(англ. **currying**\) в информатике — преобразование фун  
кции от многих аргументов в набор функций, каждая из которых является функцией от одного аргумента.

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

{% code-tabs %}
{% code-tabs-item title="Inheritance & prototype" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Context" %}
```javascript
var objA = {
  name: "Alex",
  sayName: function() {
    console.log(this.name);
  }
}
var objB = { name: "Ben", sayName: objA.sayName };
var name = "John";
var sayName = objA.sayName;

sayName();           // ?
objA.sayName();      // ?
objB.sayName();      // ?
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Context" %}
```javascript
var obj = {
    prop: 'Hi',
    fncA: function () {
        return this.prop;
    },
    fncB: () => this.prop
}
var var1 = obj.fncA();  // ???
var fnc = obj.fncA;
var val2 = fnc();      // ???
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Context" %}
```javascript
var obj = {
    prop: 'One',
    fnc: function () {
        return this.prop;
    }
};
obj.fnc.prop = 'Two';
obj.fnc();  //  ???
var fn = obj.fnc;
fn();       //  ???
obj.prop = 'Three';
obj.fnc();  //  ???
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Bind context" %}
```javascript
var poke1 = {name:'Pikachu'};
var poke2 = {name:'Chermander'};
var poke3 = {name:'Bulbasaur'};

var sayName = function(){ console.log(this.name) }

sayName.bind(poke1).bind(poke2).call(poke3);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="How to fix ?" %}
```javascript
for (var i = 0; i < 10; i++) {
    setTimeout(function () {
        console.log(i)
    }, 100);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



