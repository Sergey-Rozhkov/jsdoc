# Decorators

{% embed url="https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841" %}

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

