---
description: >-
  https://ru.hexlet.io/courses/js-functions/lessons/first-class-citizen/theory_unit
---

# First-class citizen

В языках программирования существует понятие "объекты первого рода \(или класса\)". Им обозначают элементы, которые могут быть переданы в функции, возвращены из функций и присвоены переменным \(или константам\). К таким элементам относятся любые _данные_, например числа, строки, массивы или логические значения. Обратите внимание, что сама _переменная_ \(или константа\) под это понятие не попадает, объектом первого рода считаются те данные, которые лежат в _переменной_ \(или константе\).

```javascript
// 5 — число, объект первого рода (сохранено в константе)
const num = 5;

// 2 — число, объект первого рода (аргумент функции)
// содержимое константы num — объект первого рода (аргумент функции)
// содержимое константы result — объект первого рода (возвращаемое значение)
const result = Math.pow(num, 2);
```

Описанное выше вы проделывали множество раз, и эту тему можно было бы не поднимать, если бы не одно "но". Функции тоже могут быть объектами первого рода.

#### Сохранение в переменной <a id="sohranenie-v-peremennoy"></a>

```javascript
const x = () => console.log('hey');

x(); // => hey
```

[https://repl.it/@hexlet/js-functions-first-class-citizen-definition](https://repl.it/@hexlet/js-functions-first-class-citizen-definition)

Ничего необычного, вы видели и писали подобное множество раз. Однако если считаете, что в этом коде создаётся функция `x`, то на самом деле это не так. Здесь происходят следующие две операции:

1. Создание \(определение\) функции: `() => console.log('hey')`
2. Создание константы `x` и сохранение в ней значения в виде функции: `const x =`

Этот момент нужно хорошо прочувствовать. Минимальное определение функции, которое только возможно, выглядит так: `() => {}`. Это пустая функция с пустым телом, которая не делает ничего. Присваивать её константе или нет — вопрос отдельный.

_Небольшое отступление. Функции НЕ являются примитивными значениями, они имеют сложную структуру и не могут быть сохранены в переменной как, к примеру, числа. Поэтому они хранятся по ссылке, так же как и_ [_массивы_](https://ru.hexlet.io/courses/js-arrays/lessons/references/theory_unit)_. Поэтому, условимся, что, говоря "сохранили функцию в переменной", подразумеваем "сохранили ссылку на функцию в переменной". Это никак не меняет сути излагаемого, но знать об этом стоит._

Даже не вникая в синтаксис, можно делать вывод о том, что конструкция справа от "равно" — **выражение**. И это выражение порождает функцию. В JavaScript подобные функции называют анонимными, потому что у них нет имени. Глядя на код выше, нужно понимать, что определение функции и её присваивание константе — две разных операции. Чистое определение выглядит так:

```javascript
() => console.log('hey');
```

Нет жёсткой связи между определением функции и переменной, в которой это определение было сохранено. Пока переменная содержит функцию, мы можем обращаться \(вызывать\) к этой функции через переменную. Но, если бы в нашем примере `a` была бы переменной, а не константой, то мы с лёгкостью могли бы перезаписать эту переменную другим значением:

```javascript
let a = () => console.log('hey');

a(); // => 'hey'

// перезаписали переменную другим значением — числом 10,
// теперь 'a' содержит число, а доступ к функции утерян
a = 10;
```

Мы даже можем пересохранить функцию в другой константе:

```javascript
const a = () => console.log('hey');

a(); // => 'hey'

const b = a;

b(); // => 'hey'
```

Более того, анонимную функцию можно использовать напрямую, без сохранения в константе:

```javascript
(() => console.log('hey'))(); // => hey
```

В примере мы сделали вызов функции, что называется, "на лету": сначала создали `(() => console.log('hey'))` и сразу же сделали вызов с помощью _оператора вызова функции_ `()`. При этом определение функции следует обернуть в круглые скобки \(не путать с оператором вызова функции!\), чтобы обозначить границы определения для интерпретатора, которому нужно "понимать", что конкретно вы хотите вызвать. Понятно, что после такого выражения доступ к функции будет утерян, потому что она нигде не была сохранена.

Таким образом, имя переменной, содержащей функцию, не является именем функции. Поэтому такие функции и называются "анонимными". В других языках анонимные функции нередко называют лямбда-функциями. В принципе, и в JavaScript их иногда зовут так же.

Имя переменной можно выбирать произвольно, в этом смысле анонимные функции никак не влияют на ситуацию. Более того, в отличие от именованных функций, которые будучи единожды созданными, никуда не исчезают в процессе жизни программы, анонимные функции постоянно создаются и пропадают вместе с переменными, в которые они записаны. Другими словами, анонимные функции всегда локальны относительно контекста и доступны там, где они были созданы, если не предпринимать специальных мер по их возврату.

#### Создание внутри другой функции <a id="sozdanie-vnutri-drugoy-funktsii"></a>

Раз анонимная функция — выражение, мы можем определять её в любом месте программы, допускающем использование выражений, например, в теле другой функции!

```javascript
const sum = (a, b) => {
  // определили "внутреннюю" анонимную функцию и
  // сохранили в константе innerSum
  const innerSum = (x, y) => x + y;

  // вызвали внутреннюю функцию и
  // вернули результат вызова наружу из sum
  return innerSum(a, b);
};

sum(1, 4); // 5
```

Из того факта, что анонимная функция является обыкновенным выражением, следует, что её можно передавать в другие функции в качестве аргументов и возвращать из других функций, как значения. Подробнее поговорим об этом, когда будем изучать _функции высшего порядка_.

Использование анонимных функций значительно повышает выразительные возможности языка, и в этом вы скоро убедитесь. В JavaScript анонимные функции составляют костяк любой программы. Функции, создающие функции, возвращающие функции и принимающие функции как аргументы — основной способ разрабатывать в JavaScript.

