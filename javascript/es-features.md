# ES features

* ECMAScript выходит ежегодно;
* первые пакеты обновления назывались ES1, ES2, ES3, ES4, ES5;
* новые выпуски \(начиная с 2015 года\) получили название ES2015, ES2016, ES2017 \(аббревиатура ES + год выпуска\);
* ECMAScript является стандартом, а JavaScript — это самая популярная реализация этого стандарта. Среди других реализаций можно отметить [SpiderMonkey](https://ru.wikipedia.org/wiki/SpiderMonkey), [V8](https://ru.wikipedia.org/wiki/V8_%28%D0%B4%D0%B2%D0%B8%D0%B6%D0%BE%D0%BA_JavaScript%29) и [ActionScript](https://ru.wikipedia.org/wiki/ActionScript).

### ECMAScript 2015 \(ES6\)

* `let`, `const` и блочная область видимости
* Стрелочные функции
* Параметры по умолчанию
* `Spread`/`Rest` оператор
* Расширение возможностей литералов объекта
* Восьмеричный и двоичный литералы
* Деструктуризация массивов и объектов
* Ключевое слово super для объектов
* Строковые шаблоны и разделители
* for...of против for...in
* `Map` и `WeakMap`
* `Set` и `WeakSet`
* Классы в ES6
* Тип данных `Symbol`
* Итераторы
* Генераторы
* Промисы

{% embed url="http://es6-features.org/" %}

{% embed url="https://habr.com/post/305900/" %}

### ECMAScript 2016 \(ES7\)

* Оператор возведения в степень `a ** b` идентичный `Math.pow(a, b)`
* Метод `Array.prototype.includes`, который проверяет, содержится ли переданный аргумент в массиве

### ECMAScript 2017 \(ES8\)

* Async functions for a clearer Promise syntax
* `Object.values()` to extract an array of values from an object containing name–value pairs
* `Object.entries()`, which returns an array of sub-arrays containing the names and values in an object
* `Object.getOwnPropertyDescriptors()` to return an object defining property descriptors for own properties of another object \(`.value`, `.writable`, `.get`, `.set`, `.configurable`, `.enumerable`\)
* `padStart()` and `padEnd()`, both elements of string padding
* trailing commas on object definitions, array declarations and function parameter lists
* `SharedArrayBuffer` and `Atomics` for reading from and writing to shared memory locations \(disabled in response to the [Spectre vulnerability](https://meltdownattack.com/)\).

{% embed url="https://www.sitepoint.com/es2017-whats-new/" %}

### ECMAScript 2018 \(ES9\)

* Asynchronous Iteration
* `Promise.Finally()` -  allows to specify final logic in one place rather than duplicating it within the last `.then()` and `.catch()`
* `Rest/Spread Properties` - rest parameters convert the last arguments passed to a function into an array
* `Regular Expression Named Capture Groups` - permits groups to be named using the notation `?<name>` immediately after the opening capture bracket `(`
* `Regular Expression Lookbehind Assertions` 
* `Regular Expression S (DotAll) Flag`
* `Regular Expression Unicode Property Escapes` - all syntactic restrictions related to escape sequences in template literals have been removed.

{% embed url="https://www.sitepoint.com/es2018-whats-new/" caption="" %}



