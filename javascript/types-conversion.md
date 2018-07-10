# Types conversion

{% embed data="{\"url\":\"https://learn.javascript.ru/types-conversion\",\"type\":\"link\",\"title\":\"Преобразование типов для примитивов\",\"icon\":{\"type\":\"icon\",\"url\":\"https://learn.javascript.ru/img/favicon/apple-touch-icon-precomposed.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://learn.javascript.ru/img/site\_preview\_ru\_1200x630.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

{% embed data="{\"url\":\"https://learn.javascript.ru/object-conversion\",\"type\":\"link\",\"title\":\"Преобразование объектов: toString и valueOf\",\"icon\":{\"type\":\"icon\",\"url\":\"https://learn.javascript.ru/img/favicon/apple-touch-icon-precomposed.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://learn.javascript.ru/img/site\_preview\_ru\_1200x630.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

{% embed data="{\"url\":\"https://medium.com/@frontman/%D0%BF%D1%80%D0%B8%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2-%D0%B2-js-9d6f1845ea96\",\"type\":\"link\",\"title\":\"Приведение типов в JS\",\"description\":\"Магия или простые правила?\",\"icon\":{\"type\":\"icon\",\"url\":\"https://cdn-images-1.medium.com/fit/c/304/304/1\*8I-HPL0bfoIzGied-dzOvA.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://cdn-images-1.medium.com/max/1858/1\*qLzx9tDMLoj2o9Hy15X8Fw.png\",\"width\":929,\"height\":359,\"aspectRatio\":0.38643702906350913}}" %}

{% embed data="{\"url\":\"https://medium.com/@sergeybulavyk/%D0%BF%D1%80%D0%B5%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2-%D0%B2-javascript-35a15ddfc333\",\"type\":\"link\",\"title\":\"Преобразование типов в JavaScript\",\"description\":\"Know your engines!\",\"icon\":{\"type\":\"icon\",\"url\":\"https://cdn-images-1.medium.com/fit/c/304/304/1\*8I-HPL0bfoIzGied-dzOvA.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://cdn-images-1.medium.com/max/1400/1\*CtbRlUx4gzE74L7yFaQxxg.png\",\"width\":700,\"height\":681,\"aspectRatio\":0.9728571428571429}}" %}

```javascript
var a = {key: 'foo'};
var b = {key: 'bar'};
var c = {};

c[a] = 123; 
c[b] = 345; 
console.log(c[a], c[b]); // ???
```

```javascript
var foo = {
	toString: function () {
		return "foo";
	},
	valueOf: function () {
		return 5;
	}
};

alert(foo + "bar"); // ???
alert([foo, "bar"].join("")); // ???
```

```javascript
var a = 42;
var b = "foo";

a < b; // ?
a > b; // ?
a == b; // ?
```

```javascript
const bool = new Boolean(false);
if (bool) console.log(bool);
if (bool == false) console.log(bool);
```

```javascript
var foo = {
	toString: function () {
		return 5;
	},
	valueOf: function () {
		return "foo";
	}
};
alert(foo.toString() + 1); // 6 (bad!)
alert(foo + 1); // "foo1" (no good!)
alert(+foo); // NaN (the worst!)
```

```javascript
true + false
12 / "6"
"number" + 15 + 3
15 + 3 + "number"
[1] > null
"foo" + + "bar"
'true' == true
false == 'false'
null == ''
!!"false" == !!"true"
[‘x’] == ‘x’
[] + null + 1
[1,2,3] == [1,2,3]
{}+[]+{}+[1]
!+[]+[]+![]
new Date(0) - 0
new Date(0) + 0
'b' + 'a' + + 'a'
1 + '1' - '1'
1 > 2 > 3
3 < 2 < 1
```

```javascript
function MyObj(val){
  this.val = val;
  this.valueOf = function () {
    console.log('valueOf', this.val);
    return this.val.valueOf();
  };
  this.toString = function () {
    console.log('toString', this.val);
    return this.val.toString();
  };
}

var a = new MyObj(1);
var b = new MyObj('2');

console.log(a > b);
console.log(a + b);
console.log(a, b);
```



