# Inheritance and context

## [Наследование и цепочка прототипов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

{% code-tabs %}
{% code-tabs-item title="Функциональное наследование" %}
```javascript
function SuperCar(){
    var wave = 'beep';  //  this.wave = 'ding';
    this.makeSound = function(){
        console.log(wave);
    }
}

function Car(color) {
    SuperCar.call(this);    //  SuperCar.apply(this, arguments);
    this.color = color;
}

var obj = new Car('red');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Прототипное наследование" %}
```javascript
function SuperCar(){
    var wave = 'beep';  //  this.wave = 'ding';
}
SuperCar.prototype.makeSound = function(){ console.log(this.wave); };

function Car(color) {
    this.color = color;
}
Car.prototype.func = function(){ console.log("func"); };

SuperCar.prototype.run = function (){ console.log("run"); };
// Car.prototype = new SuperCar();
Car.prototype = Object.create(SuperCar.prototype);


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

