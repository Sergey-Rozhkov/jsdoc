# ES features

* ECMAscript выходит ежегодно;
* первые пакеты обновления назывались ES1, ES2, ES3, ES4, ES5;
* новые выпуски \(начиная с 2015 года\) получили название ES2015, ES2016, ES2017 \(аббревиатура ES + год выпуска\);
* ECMAScript является стандартом, а JavaScript — это самая популярная реализация этого стандарта. Среди других реализаций можно отметить [SpiderMonkey](https://ru.wikipedia.org/wiki/SpiderMonkey), [V8](https://ru.wikipedia.org/wiki/V8_%28%D0%B4%D0%B2%D0%B8%D0%B6%D0%BE%D0%BA_JavaScript%29) и [ActionScript](https://ru.wikipedia.org/wiki/ActionScript).

### ECMAScript 2015 \(ES6\)

* `let`, `const` и блочная область видимости
* Стрелочные функции
* Параметры по умолчанию
* Spread/Rest оператор
* Расширение возможностей литералов объекта
* Восьмеричный и двоичный литералы
* Деструктуризация массивов и объектов
* Ключевое слово super для объектов
* Строковые шаблоны и разделители
* for...of против for...in
* Map и WeakMap
* Set и WeakSet
* Классы в ES6
* Тип данных Symbol
* Итераторы
* Генераторы
* Промисы

{% embed data="{\"url\":\"http://es6-features.org/\",\"type\":\"link\",\"title\":\"ECMAScript 6: New Features: Overview and Comparison\"}" %}

{% embed data="{\"url\":\"https://habr.com/post/305900/\",\"type\":\"link\",\"title\":\"ES6 по-человечески\",\"description\":\"От переводчика: Предлагаю вашему вниманию перевод краткого \(действительно краткого\) руководства по ES6. В нём можно ознакомиться с основными понятиями стандарта...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://habr.com/images/apple-touch-icon.png\",\"width\":180,\"height\":180,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://habr.com/images/habr.png\",\"width\":1200,\"height\":628,\"aspectRatio\":0.5233333333333333}}" %}

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

{% embed data="{\"url\":\"https://www.sitepoint.com/es2017-whats-new/\",\"type\":\"link\",\"title\":\"What’s new in ES2017: Async functions, improved objects and more\",\"description\":\"Craig Buckler reviews the main JavaScript updates introduced with ES2017, and also giving a brief outline of how the updating process works.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.sitepoint.com/wp-content/themes/sitepoint/assets/images/apple-touch-icon-144x144-precomposed.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.sitepoint.com/wp-content/themes/sitepoint/assets/images/icon.javascript.png\",\"width\":710,\"height\":710,\"aspectRatio\":1}}" %}

### ECMAScript 2018 \(ES9\)

* Asynchronous Iteration
* `Promise.Finally()` -  allows to specify final logic in one place rather than duplicating it within the last `.then()` and `.catch()`
* `Rest/Spread Properties` - rest parameters convert the last arguments passed to a function into an array
* `Regular Expression Named Capture Groups` - permits groups to be named using the notation `?<name>` immediately after the opening capture bracket `(`
* `Regular Expression Lookbehind Assertions` 
* `Regular Expression S (DotAll) Flag`
* `Regular Expression Unicode Property Escapes` - all syntactic restrictions related to escape sequences in template literals have been removed.

{% embed data="{\"url\":\"https://www.sitepoint.com/es2018-whats-new/\",\"type\":\"link\",\"title\":\"What’s New in ES2018\",\"description\":\"Craig looks at new features in ES2018 \(ES9\), including asynchronous iteration, Promise.finally\(\), rest/spread properties and RegEx lookbehind assertions.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.sitepoint.com/wp-content/themes/sitepoint/assets/images/apple-touch-icon-144x144-precomposed.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.sitepoint.com/wp-content/themes/sitepoint/assets/images/icon.javascript.png\",\"width\":710,\"height\":710,\"aspectRatio\":1},\"caption\":\"\"}" %}



