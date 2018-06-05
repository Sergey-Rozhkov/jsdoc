# Objects creating

* Литеральная нотация
* Оператор `new` - создает экземпляр объекта, встроенного или определенного пользователем, имеющего конструктор
* Метод `Object.create` - создаёт новый объект с указанными объектом прототипа и свойствами.
* Конструкторы объектов

{% code-tabs %}
{% code-tabs-item title="Способы создания объекта" %}
```javascript
const a = {};

const b = new Object();

const c = Object.create(null);

function User() {}
const d = new User();
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



