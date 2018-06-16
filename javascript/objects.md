# Objects

* [Свойства и Методы конструктора Object](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object)
* [Свойства и](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Properties) [Методы экземпляров Object](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Methods)

### Способы создания

* Литеральная нотация
* Оператор `new` - создает экземпляр объекта, встроенного или определенного пользователем, имеющего конструктор
* Метод `Object.create` - создаёт новый объект с указанными объектом прототипа и свойствами
* Конструкторы объектов

{% code-tabs %}
{% code-tabs-item title="Способы создания обьекта" %}
```javascript
const a = {};
​
const b = new Object();
​
const c = Object.create(null);
​
function User() {}
const d = new User();

const o = {
    property: function ([parameters]) {},
    get property() {},
    set property(value) {}
};
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Object.create polyfill" %}
```javascript
Object.myCreate = function(prototype, descriptors) {
    function F() {};
    F.prototype = prototype;
    if (typeof(descriptors) === "object") {
        for (prop in descriptors) {
            if (descriptors.hasOwnProperty((prop))) {
                F[prop] = props[prop].value;
            }
        }
    }
    return new F();
    
    // Object.defineProperties(object1, descriptors);
}

// descriptors
// {x: { value: undefined, writable: true, configurable: true, enumerable: true}}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Статические методы и свойства

```javascript
function Article() {
  Article.count++;
  //...
}
Article.count = 0;

Article.showCount = function() {
  alert( this.count );
}

// использование
new Article();
new Article();
Article.showCount();
```

### Фабричные методы

```javascript
function User(userData) {
  if (userData) { // если указаны данные -- одна ветка if
    this.name = userData.name;
    this.age = userData.age;
  } else { // если не указаны -- другая
    this.name = 'Аноним';
  }

  this.sayHi = function() {
    alert(this.name)
  };
  // ...
}

// Использование
var guest = new User();
guest.sayHi(); // Аноним

var knownUser = new User({
  name: 'Вася',
  age: 25
});
knownUser.sayHi(); // Вася
```

