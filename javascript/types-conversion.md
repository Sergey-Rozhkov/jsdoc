# Types conversion

### Материалы

{% embed url="https://learn.javascript.ru/types-conversion" %}

{% embed url="https://learn.javascript.ru/object-conversion" %}

{% embed url="https://medium.com/@frontman/%D0%BF%D1%80%D0%B8%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2-%D0%B2-js-9d6f1845ea96" %}

{% embed url="https://medium.com/@sergeybulavyk/%D0%BF%D1%80%D0%B5%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2-%D0%B2-javascript-35a15ddfc333" %}

### Объяснить код

```javascript
var a = {key: 'foo'};
var b = {key: 'bar'};
var c = {};

c[a] = 123;
c[b] = 345;
console.log(c[a], c[b], c[c]); // ?
```

```javascript
var a = 42;
var b = "foo";

a < b; // ?
a > b; // ?
a == b; // ?
```

{% code-tabs %}
{% code-tabs-item title="Boolean" %}
```javascript
const bool = new Boolean(false);
if (bool) console.log(bool);
if (bool == false) console.log(bool);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

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

{% code-tabs %}
{% code-tabs-item title="Explanation" %}
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
alert(foo + 1);            // "foo1" (no good!)
alert(+foo);               // NaN (the worst!)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="valueOf vs toString" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="valueOf vs toString" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}



