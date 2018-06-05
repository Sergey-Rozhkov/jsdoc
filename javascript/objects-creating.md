# Objects creating

* Оператор new
* Литеральная нотация
* Конструкторы объектов
* Метод Object.create

**new** - Оператор \(операторная функция\) которая создает экземпляр объекта, встроенного или определенного пользователем, имеющего конструктор.

```javascript
const a = new Object();

const b = Object.create(null);

const c = {};

function User() {}
const d = new User();
```

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

// {x: { value: undefined, writable: true, configurable: true, enumerable: true}}
```



