# RESTful API

REST (representational state transfer — «передача состояния представления») или, лучше сказать, представление данных в удобном для клиента формате. Основная идея REST в том, что каждое обращение к сервису переводит клиентское приложение в новое состояние. По сути, REST — не протокол и не стандарт, а подход, архитектурный стиль проектирования API.

## **Принципы REST**

* **Клиент-серверная архитектура** — без этого REST немыслим.
* **Любые данные — ресурс**.
* **Любой ресурс имеет ID**, по которому можно получить данные.
* **Ресурсы могут быть связаны между собой** — для этого в составе ответа передается либо ID, либо, как чаще рекомендуется, ссылка.&#x20;
* **Используются стандартные методы HTTP** (GET, POST, PUT, DELETE) — т.к. они уже заложены в составе протокола, мы их можем использовать для того, чтобы построить каркас взаимодействия с нашим сервером.
* **Сервер не хранит состояние** — это значит, сервер не отделяет один вызов от другого, не сохраняет все сессии в памяти. Если у вас есть какое-либо масштабируемое облако, какая-то ферма из серверов, которая реализует ваш сервис, нет необходимости обеспечивать согласованность состояния этих сервисов между всеми узлами, которые у вас есть. Это сильно упрощает масштабирование — при добавлении еще одного узла все прекрасно работает.

## Best Practices

### &#x20;**1. Конечные точки в URL – имя существительное, не глагол**

&#x20;Вы должны всегда использовать существительные вместо глаголов.

> _**Best Practice:**_\
> _****_Имеем единственную конечную точку, которая отвечает за все действия. В примере ниже представлена только одна конечная точка /farmers для всех операций таких как добавление, обновление, удаление. Базовые реализации имеют различные HTTP методы, которые правильно маршрутизируются для разных операций.\
> \
> • /farmers\
> • /crops\
> \
> _**Не рекомендуется:**_\
> _****_Постарайтесь избегать использования глаголов. Рекомендуется представлять операции внутри таких форматах как JSON, XML, RAML или использовать HTTP методы. Не используйте представленные ниже обозначения:\
> \
> • /getFarmers\
> • /updateFarmers\
> • /deleteFarmers\
> • /getCrops\
> • /updateCrops\
> • /deleteCrops

### &#x20;**2. Множественное число**

&#x20;Используйте множественное число для названия своих REST сервисов.

> _**Best Practice:**_\
> _****_\
> _****_• /farmers\
> • /farmers/{farmer\_id}\
> • /crops\
> • /crops/{crop\_id}\
> \
> _**Не рекомендуется:**_\
> _****_\
> _****_• /farmer\
> • /farmer/{farmer\_id}

### &#x20;3. Документация

Документирование программного обеспечения является общей практикой для всех разработчиков. Этой практики стоит придерживаться и при реализации REST приложений. Если писать полезную документацию, то она поможет другим разработчикам понять ваш код.\
Наиболее распространенным способом документирования REST приложений – это документация с перечисленными в ней конечными точками, и описывающая список операций для каждой из них. Есть множество инструментов, которые позволяют сделать это автоматически.

> Ниже представлены приложения, которые помогают документировать REST сервисы:\
> \
> • [DRF Docs](https://www.drfdocs.com)\
> • [Swagger](https://swagger.io)\
> • [Apiary](https://apiary.io)

### &#x20;4. Версия вашего приложения

_**Мультимедийный способ управления версиями:**_ Этот подход отправляет информацию о версии в заголовке каждого запроса. Когда мы изменим тип и язык мультимедиа URI, мы перейдем к рассмотрению контента на основе заголовка. Этот способ является наиболее предпочтительным вариантом для управления версиями REST приложений.

> Пример информации в заголовке:\
> \
> GET /account/5555 HTTP/1.1\
> Accept: application/vnd.farmers.v1+json\
> \
> HTTP/1.1 200 OK\
> Content-Type: application/vnd.farmers.v1+json\
> \
> В мультимедийном подходе управления версиями клиент имеет возможность выбрать, какую версию запрашивать с сервера. Этот способ выглядит предпочтительней, чем подход с URI(host/v2/farmers, host/v1/farmers), но сложность возникает при кэшировании запросов с различными версиями, которые передаются через заголовок. Говоря простыми словами, когда клиент кэширует на основе URI, это просто, но, кэширование с ключом в качестве мультимедийного типа добавляет сложности.

### 5. Пагинация

Отправка большого объема данных через HTTP не очень хорошая идея. Безусловно, возникнут проблемы с производительностью, поскольку сериализация больших объектов JSON станет дорогостоящей. Best practice является разбиение результатов на части, а не отправка всех записей сразу. Предоставьте возможность разбивать результаты на странице с помощью предыдущих или следующих ссылок.

### 6. Использование SSL

SSL должен быть! Вы всегда должны применять SSL для своего REST приложения. Доступ к вашему приложения будет осуществляется из любой точки мира, и нет никакой гарантии, что к нему будет обеспечен безопасный доступ. С ростом числа инцидентов с киберпреступностью мы обязательно должны обеспечить безопасность своему приложению.&#x20;

### 7. HTTP методы

Ниже представлены две характеристики, которые должны быть определены перед использованием HTTP метода:

* Безопасность: HTTP метод считается безопасным, когда вызов этого метода не изменяет состояние данных. Например, когда вы извлекаете данные с помощью метода GET, это безопасно, потому что этот метод не обновляет данные на стороне сервера.
* Идемпотентность: когда вы получаете один и тот же ответ, сколько раз вы вызываете один и тот же ресурс, он известен как идемпотентный. Например, когда вы пытаетесь обновить одни и те же данные на сервере, ответ будет таким же для каждого запроса, сделанного с одинаковыми данными.

![](<../.gitbook/assets/image (26).png>)

&#x20;Краткий обзор каждого метода и рекомендации по их использованию:

* `GET` - обычно используется для извлечения информации и не имеет побочных эффектов.
* `POST` - этот метод наиболее широко используется для создания ресурсов.
* `PUT` - используется для обновления ресурсов.&#x20;
* &#x20;`PATCH`  - предоставляет частичную модификацию ресурса. Например, если нужно обновить только одно поле для ресурса
* `DELETE`- этот метод используется для удаления ресурсов.
* `OPTIONS` этот метод не используется для каких-либо манипуляций с ресурсами. Но он полезен, когда клиент не знает других методов, поддерживаемых для ресурса, и используя этот метод, клиент может получить различное представление ресурса.
* `HEAD` этот метод используется для запроса ресурса c сервера. Он очень похож на метод GET, но HEAD должен отправлять запрос и получать ответ только в заголовке. Согласно спецификации HTTP, этот метод не должен использовать тело для запроса и ответа.

### &#x20;8. Эффективное использование кодов ответов HTTP

* **200 OK** — это ответ на успешные GET, PUT, PATCH или DELETE. Этот код также используется для POST, который не приводит к созданию.
* **201 Created** — этот код состояния является ответом на POST, который приводит к созданию.
* **204 Нет содержимого.** Это ответ на успешный запрос, который не будет возвращать тело (например, запрос DELETE).
* **300 Multiple Choices** — по указанному URI существует несколько вариантов предоставления ресурса по типу [MIME](https://ru.wikipedia.org/wiki/MIME), по языку или по другим характеристикам. Сервер передаёт с сообщением список альтернатив, давая возможность сделать выбор клиенту автоматически или пользователю.&#x20;
* **301 Moved Permanently** — запрошенный документ был окончательно перенесен на новый URI, указанный в поле `Location`заголовка.&#x20;
* **302 Found, 302 Moved Temporarily** — запрошенный документ временно доступен по другому URI, указанному в заголовке в поле `Location`.&#x20;
* **304 Not Modified** — используйте этот код состояния, когда заголовки HTTP-кеширования находятся в работе
* **400 Bad Request** — этот код состояния указывает, что запрос искажен, например, если тело не может быть проанализировано
* **401 Unauthorized** — Если не указаны или недействительны данные аутентификации. Также полезно активировать всплывающее окно auth, если приложение используется из браузера
* **403 Forbidden** — когда аутентификация прошла успешно, но аутентифицированный пользователь не имеет доступа к ресурсу
* **404 Not found** — если запрашивается несуществующий ресурс
* **405 Method Not Allowed** — когда запрашивается HTTP-метод, который не разрешен для аутентифицированного пользователя
* **410 Gone** — этот код состояния указывает, что ресурс в этой конечной точке больше не доступен. Полезно в качестве защитного ответа для старых версий API
* **415 Unsupported Media Type.** Если в качестве части запроса был указан неправильный тип содержимого
* **422 Unprocessable Entity** — используется для проверки ошибок
* **429 Too Many Requests** — когда запрос отклоняется из-за ограничения скорости.

[Полный список кодов состояния HTTP](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA\_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2\_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F\_HTTP)

