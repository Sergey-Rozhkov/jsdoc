# Inheritance and context

## [Наследование и цепочка прототипов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

Наследование – это создание новых «классов» на основе существующих.

* Прототипное
* [Функциональное](https://learn.javascript.ru/functional-inheritance)

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
Car.prototype = new SuperCar();
Car.prototype.sayYes = function(){ console.log("Yes!"); };
// Car.prototype = Object.create(SuperCar.prototype);

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
// -- vs --
function User(name) {
  this.name = name;
  this.sayName = function() {
    console.log('Name: ' + this.name);
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Функции привязки контекста

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

## Карринг

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

