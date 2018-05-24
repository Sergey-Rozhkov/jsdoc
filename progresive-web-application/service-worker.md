# Service Worker

Полезные ссылки:

[https://www.youtube.com/watch?v=jVfXiv03y5c](https://www.youtube.com/watch?v=jVfXiv03y5c)

[https://www.sitepoint.com/retrofit-your-website-as-a-progressive-web-app/\#step3createaserviceworker](https://www.sitepoint.com/retrofit-your-website-as-a-progressive-web-app/#step3createaserviceworker)

Скрипт выполняет роль своеобразного proxy между браузером и вебом. Скрипт может работает независимо от приложения, т.е. может быть активен даже когда приложение не активно.

Основные функции:

1.  Работа по кэшированию.
2.  Обработка online-запросов.
3.  Хранилище информации для offline-работы.
4.  Поддержка push-сообщений.

### Включение скрипта в приложения можно суммировать:

1.  Набросать html страницу.
2.  Запустить локальный сервер.
3.  Регистрация ServiceWorker: JS-скрипт файл проверяет поддержку браузером этой технологии. Для этого регистрируем файл \(например, с названием “sw.js”\), на первом этапе он может быть пустым. Если ответ от браузера положительный, то происходит регистрация скрипта “sw.js”, в противном случае приложение отображается как обычно без дополнительных улучшений.
4. Затем переходим в файл “sw.js” где будет происходить основные три события ServiceWorker: **установка**, **активация** и **кеширование.**

```text

if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/sw.js', { scope: '/sw-test/' }).then(function(reg) {
    // регистрация сработала
    console.log('Registration succeeded. Scope is ' + reg.scope);
  }).catch(function(error) {
    // регистрация прошла неудачно
    console.log('Registration failed with ' + error);
  });
}
```

### **Стадия кеширования**:

Информацию по состоянию кэша можно просмотреть: Chrome – Инструменты разработчика – Application. В заголовке html-страницы можно задавать длительность хранения кэша:

Cache-Control: must-revalidate, max-age=86400

Простейший файл для работы с CACHE API должен включать в себя:

1. var **version** – обозначение версии вашей программы.
2. var **CACHE** – хранилище кешированной информации.
3. var **offlineURL** – это адрес страницы, которая не кеширована или не посещалась ранее. Т.е. это то, что будет показываться пользователю при отсутствии связи.
4. var **installFilesEssential** – это массив со списком файлов, которые обеспечивают функционирование страницы offline. Туда должны входить: **offlineURL, “/”** and **“index.html”** \(адрес домашней страницы\). Включение CSS и других файлов рекомендуется, но не обязательно. Первый элемент – корневой каталог.

```text
const
  version = '1.0.0',
  CACHE = version + '::PWAsite',
  offlineURL = '/offline/',
  installFilesEssential = [
    '/',
    '/manifest.json',
    '/css/styles.css',
    '/js/main.js',
    '/js/offlinepage.js',
    '/images/logo/logo152.png'
  ].concat(offlineURL),
  installFilesDesirable = [
    '/favicon.ico',
    '/images/logo/logo016.png',
    '/images/hero/power-pv.jpg',
    '/images/hero/power-lo.jpg',
    '/images/hero/power-hi.jpg'
  ];
```

1. Затем создаем функцию, которая кеширует файл используя CACHE API \([https://developer.mozilla.org/en-US/docs/Web/API/Cache](https://developer.mozilla.org/en-US/docs/Web/API/Cache) \). Функция возвращает только те данные, которые включены в массив **installFilesEssential.**

```text
function installStaticFiles() {
  return caches.open(CACHE)
    .then(cache => {
      // кешируем дополнительные данные
      cache.addAll(installFilesDesirable);
      // кешируем основные данные
      return cache.addAll(installFilesEssential);
    });
}
```

### **Стадия установки:**

1\) Прикрепляем событие **install**. Метод **waitUntil\(\)** обеспечивает установку и активацию скрипта ServiceWorker только после кеширования необходимых файлов \(**installFilesEssential\(\)**\):

```text
self.addEventListener('install', event => {
  console.log('service worker: install');
  // cache core files
  event.waitUntil(
    installStaticFiles()
    .then(() => self.skipWaiting())
  );
});
```

2\) Отчистка от старого кеша **clearOldCaches\(\)**: эта функция не обязательна, но крайне желательна. Рекомендуется добавлять перед стадией активации:

```text
function clearOldCaches() {
  return caches.keys()
    .then(keylist => {
      return Promise.all(
        keylist
          .filter(key => key !== CACHE)
          .map(key => caches.delete(key))
      );
    });
}
```

### **Стадия Активации**:

Запуск рабочего serviceWorker происходит вызовом **self.clients.claim\(\)**:

```text
self.addEventListener('activate', event => {
  console.log('service worker: activate');
    // delete old caches
  event.waitUntil(
    clearOldCaches()
    .then(() => self.clients.claim())
    );
});
```

### **Обновление данных**:

происходит при запросе к сети с помощью события fetch и метода **respondWith\(\)**. Происходит в три этапа:

1. Извлечение целевой информации из кэша.
2. Если пункт 1 провалился, то данные загружаются из сети с помощью FETCH API и кэшируются\(нужно отметить, что FETCH API запрос и fetch событие в serviceWorker – два различных процесса\).
3. Если пункт 1 и 2 провалились – выдается соответствующий комментарий **offlineAsset\(\)**. Может быть заполнена дополнительными функциями.

```text
self.addEventListener('fetch', event => {
  // abandon non-GET requests
  if (event.request.method !== 'GET') return;
  let url = event.request.url;
  event.respondWith(
    caches.open(CACHE)
      .then(cache => {
        return cache.match(event.request)
          .then(response => {
            if (response) {
              // return cached file
              console.log('cache fetch: ' + url);
              return response;
            }
            // make network request
            return fetch(event.request)
              .then(newreq => {
                console.log('network fetch: ' + url);
                if (newreq.ok) cache.put(event.request, newreq.clone());
                return newreq;
              })
              // app is offline
              .catch(() => offlineAsset(url));
          });
      })
  );
});
```



