# Write code

Напишите программу, которая выводит на экран числа от 1 до 100. При этом вместо чисел, кратных трем, программа должна выводить слово «Fizz», а вместо чисел, кратных пяти — слово «Buzz». Если число кратно и 3, и 5, то программа должна выводить слово «FizzBuzz»

Напишите функцию, принимающую на вход строку, и возвращающую первый символ, который встречается в строке только один раз. Если это буква, то она должна быть в том регистре, в котором она встретилась в строке. Например, для строки **mAmaN** вернуть **N**. Если все символы встречаются больше одного раза, вернуть пустую строку.  
`firstNonRepeatingLetter('mAmaN') === 'N'  
firstNonRepeatingLetter('a') === 'a'  
firstNonRepeatingLetter('paPA') === ''  
firstNonRepeatingLetter('Go hang a salami, I\'m a lasagna hog!') === ','`

Напишите код функции **sum**  
`sum(1)(2)() // 3  
sum(1)(2)(3)() // 6   
sum(2)(2)(2)(2)(2)() // 10`

Напишите код функции **myFunc**  
`myFunc(sum)(2)(3); // 5  
myFunc(mul)(2)(3); // 6`

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

Напишите код функции **isMonoArr** которая проверяет массив на монотонность

```javascript
var a1 = [1,1,2]; // true
var a2 = [3,2,0]; // true
var a3 = [1,1,1]; // true
var a4 = [1,2,0]; // false
var a5 = [1,2,3,1,2,3]; // false
var a6 = [4,1,1,4]; // false

console.log(isMonoArr(a1));
console.log(isMonoArr(a2));
console.log(isMonoArr(a3));
console.log(isMonoArr(a4));
console.log(isMonoArr(a5));
console.log(isMonoArr(a6));

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

Напишите реализацию паттерна Singleton

Напишите реализацию паттерна Factory

Напишите реализацию паттерна Module

