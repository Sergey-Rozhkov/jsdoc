# Web App Manifest

## **Манифест веб-приложения \(Web** **App** **Manifest\).**

Манифест веб-приложения \(Web App Manifest\) – это **JSON-файл**, который содержит краткую информацию о приложении \(такую как имя, авторство, иконку и описание\). Цель манифеста — установить веб-приложение на домашний экран устройства с минимальными усилиями и без лишних телодвижений со стороны пользователя. Манифест веб-приложения является составной частью коллекции веб-технологий используемых для создания прогрессивного веб-приложения \([https://developer.mozilla.org/en-US/Apps/Progressive](https://developer.mozilla.org/en-US/Apps/Progressive) \).

* Ссылка на документацию: https://developer.mozilla.org/ru/docs/Web/%D0%9C%D0%B0%D0%BD%B8%D1%84%D0%B5%D1%81%D1%82
* Ссылка на ролик: https://www.youtube.com/watch?v=4kx6QgK4vJE

Для **внедрения манифеста** на страницу приложения необходимо включить тэг ссылки в заголовке html документа: &lt;link rel=”manifest” href=”/manifest.webmaifest”&gt;

**Проверку правильности** заполнения манифеста можно осуществить с помощью Manifest Validator - [https://manifest-validator.appspot.com/](https://manifest-validator.appspot.com/)

### **Пример манифеста:**

```text
{
  "name"              : "PWA Website",
  "short_name"        : "PWA",
  "description"       : "An example PWA website",
  "start_url"         : "/",
  "display"           : "standalone",
  "orientation"       : "any",
  "background_color"  : "#ACE",
  "theme_color"       : "#ACE",
  "icons": [
    {
      "src"           : "/images/logo/logo072.png",
      "sizes"         : "72x72",
      "type"          : "image/png"
    },
    {
      "src"           : "/images/logo/logo152.png",
      "sizes"         : "152x152",
      "type"          : "image/png"
    },
    {
      "src"           : "/images/logo/logo192.png",
      "sizes"         : "192x192",
      "type"          : "image/png"
    },
    {
      "src"           : "/images/logo/logo256.png",
      "sizes"         : "256x256",
      "type"          : "image/png"
    },
    {
      "src"           : "/images/logo/logo512.png",
      "sizes"         : "512x512",
      "type"          : "image/png"
    }
  ]
}
```

### При написании Манифеста существует **список обязательных параметров** для заполнения:

1. name.
2. short\_name – предоставляет короткое удобочитаемое имя приложения.
3. start\_url – определяет URL, который загружается, когда пользователь запустил приложение с устройства.
4. icons – определяет массив объектов изображений, которые могут использованы как иконки приложения в различных контекстах. Этот параметр представляет собой обьект \(массив обектов – если речь идет о разных устройствах\) из необходимых свойств: “src”, “size”,  “type”.
5. background\_color – это значение повторяет то, что уже доступно в стилях приложения, но может быть использовано браузерами для отрисовки цвета фона приложения после того, как манифест станет доступен, но до того, как стили загрузятся.
6. display – определяет предпочтительный для разработчика режим отображения приложения \(используется все доступное пространство экрана, открывается в обычной вкладке браузера, выглядит как обычное приложение\).
7.  orientation – определяет ориентацию по умолчанию для всех верхних уровней [контекстов браузера](https://developer.mozilla.org/ru/docs/%D0%A1%D0%BB%D0%BE%D0%B2%D0%B0%D1%80%D1%8C/Browsing_context) приложения.
8. theme-color – определяет цвет темы по умолчанию для приложения.
9. description – обеспечивает общее описание того, что делает приложение.
10. “name”  - Предоставляет удобочитаемое имя для приложения, предназначенное для отображения для пользователя, например, в списке других приложений или как подпись к иконке.
11. “lang” - Определяет основной язык параметров `name` и `short_name`. Является строкой, содержащей единственный языковой тег.

MDN предоставляет полный список всех свойств.

