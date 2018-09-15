# Event delegation

{% embed data="{\"url\":\"https://developer.mozilla.org/ru/docs/Web/Events\",\"type\":\"link\",\"title\":\"Event reference\",\"description\":\"События DOM присылаются чтобы уведомить код о том, что интересующие его действия произошли. Каждое событие представляет объект, который базируется на интерфейсе Event и может иметь дополнительные поля и/или функции, позволяющие получить дополнительную информацию о том, что случилось. События могут описывать всё, что угодного от простых действий пользователя до действий автоматизированной системы рассылки уведомлений, создаваемых моделью формирования экрана.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://developer.mozilla.org/static/img/favicon144.e7e21ca263ca.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://developer.mozilla.org/static/img/opengraph-logo.72382e605ce3.png\",\"width\":600,\"height\":600,\"aspectRatio\":1}}" %}

* **EventTarget.addEventListener\(type, listener\[, useCapture\]\)**
  * Регистрирует обработчик события, вызванного на `EventTarget`. `EventTarget` должен быть либо существующим элементом в документе, либо  `Document`, либо `Window`, либо любым другим объектом, который поддерживает события \(такой, как `XMLHttpRequest`\).
* **EventTarget.dispatchEvent\(\)**
  * Отправляет событие в общую систему событий. Это событие подчиняется тем же правилам поведения "Захвата" и "Всплывания" как и непосредственно инициированные события.
* **Event.preventDefault\(\)**
  * Отменяет событие, если оно отменяемое, без остановки дальнейшего распространения этого события.
* **Event.stopPropagation\(\)**
  * Прекращает дальнейшую передачу текущего события.
* **Event.stopImmediatePropagation\(\)**
  * Останавливает цепочку вызова событий для последующих слушателей DOM элемента.

[Event delegation demo](https://codepen.io/SitePoint/pen/jmXdpz)

![Capturing &amp;gt; Targeting &amp;gt; Bubbling](../.gitbook/assets/event.png)

{% embed data="{\"url\":\"http://stepansuvorov.com/blog/2013/05/%D0%BE%D1%82%D0%BB%D0%B8%D1%87%D0%B8%D0%B5-preventdefault-stoppropagation-%D0%B8-stopimmediatepropagation/\",\"type\":\"link\",\"title\":\"Отличие preventDefault, stopPropagation и stopImmediatePropagation \| Stepan Suvorov Blog\"}" %}

