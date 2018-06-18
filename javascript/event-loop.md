---
description: Модель событийного цикла
---

# Event loop

{% embed data="{\"url\":\"https://youtu.be/8cV4ZvHXQL4\",\"type\":\"video\",\"title\":\"Про цикл событий в JavaScript или \\\"как на самом деле работает асинхронность\\\"?\",\"description\":\"\(Перевод от MakeWeb.me\) Этот доклад Филипа Робертса с JSConf проясняет очень важные моменты по поводу работы JS в браузере \(и других средах тоже, кстати\).\\n\\nРечь пойдет о цикле событий, и о том, как же на самом деле выполняются колбэки в AJAX-запросах, setTimeout и других всем известных возможностях, предоставляемых разработчику средой выполнения.\\n\\nАвтор перевода и озвучки:\\nНикита Красник \(http://vk.com/xenongattz\)\\n\\nСсылка на видео-источник: \\nhttps://www.youtube.com/watch?v=8aGhZQkoFbQ\\n\\n===\\nЕсли нравится то что мы делаем, то можешь поддержать проект на You.Support: https://you.support/MakeWeb\\n\\n===\\nПерсональные уроки по веб-разработке. Доведение до результата с нуля. Закрытие пробелов в знаниях и умениях. Обучение на реальных заказах.\\n\\nПодробности и отзывы: http://bit.ly/mw\_webdev\_lessons\\n\\n===\\nMakeWeb ВКонтакте: http://bit.ly/mw\_vk\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.youtube.com/yts/img/favicon\_144-vfliLAfaB.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://i.ytimg.com/vi/8cV4ZvHXQL4/maxresdefault.jpg\",\"width\":1280,\"height\":720,\"aspectRatio\":0.5625},\"embed\":{\"type\":\"player\",\"url\":\"https://www.youtube.com/embed/8cV4ZvHXQL4?rel=0&showinfo=0\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://www.youtube.com/embed/8cV4ZvHXQL4?rel=0&amp;showinfo=0\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

{% embed data="{\"url\":\"https://developer.mozilla.org/ru/docs/Web/JavaScript/EventLoop\",\"type\":\"link\",\"title\":\"Параллельная модель и цикл событий.\",\"description\":\"Параллелизм в JavaScript основывается на модели \\\"событийного цикла\\\". Эта модель отличается от модели других языков, например C или Java.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://developer.mozilla.org/static/img/favicon144.e7e21ca263ca.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://developer.mozilla.org/static/img/opengraph-logo.72382e605ce3.png\",\"width\":600,\"height\":600,\"aspectRatio\":1}}" %}

{% embed data="{\"url\":\"https://youtu.be/j4\_9BZezSUA\",\"type\":\"video\",\"title\":\"Jake Archibald: все что я знаю про Event Loop в JavaScript \(2018\)\",\"description\":\"\(Перевод от MakeWeb.me\) Джейк Арчибальд это один из крутейших ребят в мире JS и веб-дева. В этом выступлении он рассказывает про самые непонятные части JS:\\n- цикл событий \(event loop\);\\n- очереди задач \(task queue\);\\n- цикл рендеринга \(Request Animation Frame, Style Calculation, Layout, Paint\);\\n- микротаски \(microtasks\);\\nи много другого интересного и полезного.\\n\\nАвтор перевода и озвучки: Никита Красник \(http://vk.com/xenongattz\)\\nСсылка на видео-источник: https://www.youtube.com/watch?v=cCOL7MC4Pl0\\n\\n===\\nЕсли нравится то что мы делаем, то можешь поддержать проект на You.Support: https://you.support/MakeWeb\\n\\n===\\nПерсональные уроки по веб-разработке. Доведение до результата с нуля. Закрытие пробелов в знаниях и умениях. Обучение на реальных заказах.\\n\\nПодробнее в видео:\\nhttps://www.youtube.com/watch?v=OrA-p9-8WGE\\n\\nОтзывы:\\nhttp://bit.ly/mw\_webdev\_lessons\\n\\n===\\n≥ Сайт: http://makeweb.me\\n≥ ВКонтакте: http://vk.com/makewebme\\n≥ Facebook: http://facebook.com/makewebme\\n≥ Twitter: http://twitter.com/makewebme\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.youtube.com/yts/img/favicon\_144-vfliLAfaB.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://i.ytimg.com/vi/j4\_9BZezSUA/maxresdefault.jpg\",\"width\":1280,\"height\":720,\"aspectRatio\":0.5625},\"embed\":{\"type\":\"player\",\"url\":\"https://www.youtube.com/embed/j4\_9BZezSUA?rel=0&showinfo=0\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://www.youtube.com/embed/j4\_9BZezSUA?rel=0&amp;showinfo=0\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

[https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/)

### Объясните код

```javascript
console.log(1);
setTimeout(function() {
  console.log(2); 
})
console.log(3);
```

```javascript
console.log('log one');
setTimeout(() => console.log('timeout'));
Promise.resolve().then(() => console.log('promise'));
console.log('log two');
```

```javascript
(function () {
    console.log(1);
    setTimeout(() => console.log(2), 1000);
    setTimeout(() => console.log(3), 0);
    Promise.resolve(true).then(() => console.log(4));
    console.log(5);
})();
```

```javascript
console.log('script start');
setTimeout(function () {
    console.log('setTimeout');
}, 0);
Promise.resolve()
    .then(function () {
        console.log('promise1');
    })
    .then(function () {
        console.log('promise2');
    });
console.log('script end');
```



