# Write code

{% embed url="https://github.com/vladborsh/js-developer-interview\#exercises" %}

Напишите функцию **F**, так чтобы **new F === F**

Напишите программу, которая выводит на экран числа от 1 до 100. При этом вместо чисел, кратных трем, программа должна выводить слово «Fizz», а вместо чисел, кратных пяти — слово «Buzz». Если число кратно и 3, и 5, то программа должна выводить слово «FizzBuzz»

Напишите функцию, принимающую на вход строку, и возвращающую первый символ, который встречается в строке только один раз. Если это буква, то она должна быть в том регистре, в котором она встретилась в строке. Например, для строки **mAmaN** вернуть **N**. Если все символы встречаются больше одного раза, вернуть пустую строку.  
`firstNonRepeatingLetter('mAmaN') === 'N'  
firstNonRepeatingLetter('a') === 'a'  
firstNonRepeatingLetter('paPA') === ''  
firstNonRepeatingLetter('Go hang a salami, I\'m a lasagna hog!') === ','`

Напишите код функции `sum`, количество слагаемых не ограничено  
`sum(1)(2)() // 3  
sum(1)(2)(3)() // 6   
sum(2)(2)(2)(2)(2)() // 10`

```javascript
let f = i => j => j ? f(i + j) : i
```

```javascript
const add = (a) => {
    let sum = a;
    const func = (b) => {
        if (b) {
            sum += b;
            return func;
        } else {
            return sum;
        }
    };
    return func;
};
```

Напишите код функции `sum`, количество слагаемых не ограничено  
`sum(1)(2) // 3  
sum(1)(2)(3) // 6   
sum(2)(2)(2)(2)(2) // 10`

```javascript
const add = (a) => {
    let sum = a;
    const func = (b) => {
        sum += b;
        return func;
    };
    func.valueOf = () => sum;
    return func;
};
```

Напишите код функции **myFunc**  
`myFunc(sum)(2)(3); // 5  
myFunc(mul)(2)(3); // 6`

```javascript
const myFunc = f => a => b => f(a,b)
```

Напишите код функции **test**, которая будет проверять корректность расстановки скобок  
`test('[]()<>') // => true  
test('[]()<)') // => false  
test('[(<>)]') // => true  
test('[(<>])') // => false`

Напишите код функции проверки анаграммы  
`anagram('xyz','zyx'); // true  
anagram('xyz','xyzx'); // false`

Напишите код функции **intersect** которая выводит общие элементы массива  
`var a = [1, 2, 4, 5, 7, 9];  
var b = [1, 3, 5, 8, 9, 15];  
console.log(intersect(a, b));  //  [1,5,9]`

```javascript
function intersect(arr1, arr2) {
    // ...
}
```

Напишите код функции **isMonoArr** которая проверяет массив на монотонность

```javascript
console.log(isMonoArr([1,1,2])); // true
console.log(isMonoArr([3,2,0])); // true
console.log(isMonoArr([1,1,1])); // true
console.log(isMonoArr([1,2,0])); // false
console.log(isMonoArr([1,2,3,1,2,3])); // false
console.log(isMonoArr([4,1,1,4])); // false

function isMonoArr(arr) {
  if (arr.length < 3) {
    return true;
  }
  
  var x = 'same';
  
  for (var i=0; i<arr.length; i++) {
    if (arr[i]>arr[i+1]) {
      if (x === 'inc') {
        return false;
      } else {
        x = 'dec';
      }
    } else if (arr[i]<arr[i+1]) {
      if (x === 'dec') {
        return false;
      } else {
        x = 'inc';
      }
    }
  }

  return true;
}
```

Напишите код функции **reverse** \(без использования строк, массивов, циклов\) ?

```javascript
console.log(reverse(12345)); // 54321

function reverse(num, result = 0){
  if(num < 10) {
    return result*10 + num;
  } else {
    return reverse(Math.floor(num / 10), result*10 + num%10);
  }
}
```

```javascript
function reverse(num, result = 0){
  return (num < 10) 
    ? result*10 + num
    : reverse(Math.floor(num / 10), result*10 + num%10);
}
```

Напишите полифил на функцию `filter`

```javascript
[1,2,3,4].filter((num)=>{ return num > 3}) // >[4]

Array.prototype.filter = function (cb) {
  var result = [];

  for(const el of this) {
    if (cb(el)) {
      result.push(el);
    }
  }

  return result;
}
```

Напишите функцию `reverse`

```javascript
reverse(5,2,3) // -> '325'
reverse(1, 2, 3, 4, 5); // -> '54321'

function reverse() {
    return Array.prototype.slice.call(arguments)
      .reverse()
      .reduce((sum, val) => '' + sum + val);
}
```

```javascript
var str2 = 'al8ex jo22hn mary3' // 'mary3 al8ex jo22hn'

var res2 = str2
  .split(' ')
  .sort((a, b) => a.replace(/\D/g, '') - b.replace(/\D/g, ''))
  .join(' ');
```

Напишите реализацию паттерна Singleton

Напишите реализацию паттерна Factory

Напишите реализацию паттерна Module

