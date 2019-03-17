---
description: 'https://developer.mozilla.org/ru/docs/Web/JavaScript/Data_structures'
---

# Types

### Data types <a id="&#x422;&#x438;&#x43F;&#x44B;_&#x434;&#x430;&#x43D;&#x43D;&#x44B;&#x445;"></a>

* 6 типов данных являются примитивами:
  * [Boolean](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/Boolean) \(Булев, Логический тип\)
  * [Null](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/Null) \(Null тип \)
  * [Undefined](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/undefined) \(Неопределенный тип\)
  * [Number](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/Number) \(Число\)
  * [String](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/%D0%A1%D1%82%D1%80%D0%BE%D0%BA%D0%B0) \(Строка\)
  * [Symbol](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/Symbol) \(в ECMAScript 6\)
* и [Object](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/Object) \(Объект\)

Все типы данных в JavaScript, кроме объектов, являются иммутабельными \(значения не могут быть модифицированы, а только перезаписаны новым полным значением\). Например, в отличии от C, где строку можно по символьно корректировать, в JavaScript строки пересоздаются только полностью. Значения таких типов называются "примитивными значениями".

![Value Type and Reference Type](../../.gitbook/assets/image%20%2841%29.png)

### Objects

**Свойство-значение**  
Ассоциирует ключ со значением, и имеет следующие атрибуты:

| Атрибут | Тип | Описание | Значение по умолчанию |
| :--- | :--- | :--- | :--- |
| \[\[Value\]\] | Любой тип JavaScript | Значение, возвращаемое при обращении к свойству. | undefined |
| \[\[Writable\]\] | Boolean | Если `false`, то \[\[Value\]\] свойства не может быть изменено. | false |
| \[\[Enumerable\]\] | Boolean | Если `true`, свойство будет перечислено в цикле [for...in](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/for...in). Смотрите подробнее  [Перечисляемость и владение свойствами](https://developer.mozilla.org/ru/docs/Web/JavaScript/Enumerability_and_ownership_of_properties). | false |
| \[\[Configurable\]\] | Boolean | Если `false`, то свойство не может быть удалено, а его атрибуты, кроме \[\[Value\]\] и \[\[Writable\]\] не могут быть изменены. | false |

**Свойство-акцессор**  
Ассоциирует ключ с одной из двух функций-акцессоров \(геттер и сеттер\) для получения или изменения значения свойства, и имеет следующий атрибуты:

| Атрибут | Тип | Описание | Значение по умолчанию |
| :--- | :--- | :--- | :--- |
| \[\[Get\]\] | Function или undefined | Функция вызывается без параметров, и возвращает значение свойства, каждый раз, когда происходит чтение свойства. Смотрите также [`get`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/get). | undefined |
| \[\[Set\]\] | Function или undefined | Функция вызывается с одним аргументом, содержащим присваиваемое значение, каждый раз, когда происходит попытка присвоить свойству новое значение. Смотрите также [`set`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/set). | undefined |
| \[\[Enumerable\]\] | Boolean | Если `true`, свойство будет перечислено в цикле [for...in](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/for...in). | false |
| \[\[Configurable\]\] | Boolean | Если `false`, то свойство не может быть удалено, и не может быть преобразовано в свойство-значение. | false |

### Set and Map

Эти наборы данных используют ссылку на объект в качестве ключа, и введены в JavaScript с приходом ECMAScript Edition 6. [`Set`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Set) и [`WeakSet`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) являют собой набор уникальных объектов, в то время как [`Map`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Map) и [`WeakMap`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/WeakMap) ассоциируют с объектом \(выступающим в качестве ключа\) некоторое значение. Разница между Map и WeakMap заключается в том, что только у Map ключи являются перечисляемыми. Это позволяет оптимизировать сборку мусора для WeakMap.

### Mutable and immutable data

