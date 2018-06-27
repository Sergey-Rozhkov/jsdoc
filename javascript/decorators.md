# Decorators

{% embed data="{\"url\":\"https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841\",\"type\":\"link\",\"title\":\"Exploring EcmaScript Decorators\",\"description\":\"Iterators, generators and array comprehensions; The similarities between JavaScript and Python continue to increase over time and I for…\",\"icon\":{\"type\":\"icon\",\"url\":\"https://cdn-images-1.medium.com/fit/c/304/304/1\*YPxqkb8PlWYBtLLJiPWNbg.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://cdn-images-1.medium.com/max/2000/1\*Ifm00n-npUdYWTDbZag3rQ.png\",\"width\":1200,\"height\":633,\"aspectRatio\":0.5275}}" %}

{% code-tabs %}
{% code-tabs-item title="Decorator" %}
```javascript
function memoize(target, name, descriptor) {
    // ..
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="A simple class decorator" %}
```javascript
@annotation
class MyClass { }

function annotation(target) {
   // Add a property on target
   target.annotated = true;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="A simple method decorator" %}
```javascript
class MyClass {
  @enumerable(false)
  method() { }
}

function enumerable(value) {
  return function (target, key, descriptor) {
     descriptor.enumerable = value;
     return descriptor;
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

```javascript
class Foo {
  @function (target, key, descriptor) {   
    descriptor.writable = false; 
    return descriptor; 
  }
  bar() {
    
  }
}
```

