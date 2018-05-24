# IndexedDB

IndexedDB — JavaScript-основанная объектно-ориентированная база данных которая хранится на **стороне клиента** и предназначена для работы с большими массивами данных \(ограничение только в размерах жесткого диска\). IndexedDB позволяет сохранять и возвращать объекты, которые были проиндексированы с ключом; любой объект, поддерживаемый структурированным алгоритмом клонирования может быть сохранен.

Ссылки на документацию:

1. [https://developer.mozilla.org/ru/docs/IndexedDB/Using\_IndexedDB](https://developer.mozilla.org/ru/docs/IndexedDB/Using_IndexedDB)
2. [https://developer.mozilla.org/en-US/docs/Web/API/IDBDatabase/objectStoreNames](https://developer.mozilla.org/en-US/docs/Web/API/IDBDatabase/objectStoreNames)

### Типичная схема работа с базой:

1\) Открываем базу данных. 

```javascript
window.indexedDB = window.indexedDB || window.mozIndexedDB || window.webkitIndexedDB || window.msIndexedDBwindow.indexedDB = window.indexedDB || window.mozIndexedDB || window.webkitIndexedDB || window.msIndexedDB;
window.IDBTransaction = window.IDBTransaction || window.webkitIDBTransaction || window.msIDBTransaction || {READ_WRITE: "readwrite"}; // This line should only be needed if it is needed to support the object's constants for older browsers
window.IDBKeyRange = window.IDBKeyRange || window.webkitIDBKeyRange || window.msIDBKeyRange;
	
if (!window.indexedDB) {
	window.alert("Your browser doesn't support a stable version of IndexedDB. Such and such feature will not be available.");
}

var request = indexedDB.open("имя базы", "версия базы - в целых числах");
```

Обратите внимание, что 9-я строка кода не запускает открытие базы. Она всего-навсего возвращает обьект IDBOpenDBRequest который содержит положительный результат открытия или ошибку.

Противоположная команда **.close\(\)** необходима для закрытия базы данных.

2\) Затем записываем шаблон работы с базой, которая содержит три обязательных метода:

2.1 request. onerror\(\) - здесь происходит процесс обработки ошибки

```text
request.onerror = function(event) {
  	// Что-то делаем с ошибкой
};
```

2.2 request.onsuccess\(\) - здесь происходит основная работа с данными. Например, сохраняем данные в переменную и запускаем функцию для их отображения на странице.

```text
request.onsuccess = function(event) {
   	db = DBOpenRequest.result;
    displayData();
};
```

2.3 request.onupgradeneeded\(\) - Здесь мы создаем базу при самом первом запуске. Таким образом, жизненный цикл при первом запуске начинается из этого метода и только затем передается на request.onsuccess. Также, если версия базы данных была изменена, то  этот метод стартует первым. Кроме того, это единственное место, в котором мы можем повлиять на структуру базы, удалить или создать новое хранилище с помощью метода **createObjectStore\(\)** .

```text
request.onupgradeneeded = function(e){
	var db = e.currentTarget.result.createObjectStore("myObjectStore", { keyPath: "key" });
}
```

### Работа с данными:

Любые операции с записями в IndexedDB происходят в рамках транзакции. Транзакция открывается методом **transaction\(\["имя хранилища"\], "режим доступа"**\). В методе необходимо указать какие ObjectStore вам нужны и режим доступа: чтение \("**readonly**"\), чтение и запись \("**readwrite**"\). У этой операции также возможны три состояния:

```text
var transaction = db.transaction([имя хранилища], "readonly")
	transaction.oncomplete = function(event) {
  		alert("All done!");
	};

	transaction.onerror = function(event) {
  
	};

	var objectStore = transaction.objectStore("customers");
		for (var i in customerData) {
			var request = objectStore.add(customerData[i]);
			request.onsuccess = function(event) {
			// event.target.result == customerData[i].ssn;
		};
```

Теперь, когда у нас есть открытая транзакция, мы можем получить наш ObjectStore у которого есть следующие методы для работы с записями:

* add — добавляет строго новую запись, если попытаться добавить запись с уже существующим ключом, то получим ошибку;
* put — перезаписывает или создает новую запись по указанному ключу;
* get — возвращает запись по ключу;
* delete — удаляет запись по указанному ключу.

### Варианты поиска по базе.

1\) Единичный поиск по уникальному ключу: осуществляеься с помощью get\(\).

2\) Извлечение всех данных: Метод **get** удобно использовать, если вы знаете ключ по которому хотите получить данные. Если вы хотите пройти через все записи в ObjectStore, то можно воспользоваться **Cursor**:

```text
var customers = [];
objectStore.openCursor().onsuccess = function(event) {
	var cursor = event.target.result;
	if (cursor) {
		customers.push(cursor.value);
		cursor.continue();
	} else {
		alert("Got all customers: " + customers);
	}
};
```

Курсор это обьект уровнем выше, он содержит два поля:

* cursor.key
* cursor.value - поля с данными

3\) Выборочный поиск по ключевым словам, колонкам, обьектам происходит с помощью **index**. Для этого необходимо два действия:

3.1 Создание возможности поиска по index. Этот код прописывается в request.onupgradeneeded. Первый аргумент - это имя индекса, второй - путь \(колонка\), третий аргумент - это уникальность первого аргумента в БД.

```text
var objectStore = thisDB.createObjectStore("customers", {autoIncrement: true});
	objectStore.createIndex("name", "name", {unique:false})
```

3.2 Прописывание самого кода поиска этот код прописывается в отдельной функции.

```text
var transaction = db.transaction(["test"], "readonly");
var store = transaction.objectStore("test");
var index = store.index("name");
var request = index.get(name);
request.onsuccess = function(e){...}
```

4\) Поиск между граничными значениями можно осуществить с помощью **IDBKeyRang\(\)**. Более детально по ключевым методами - добро пожаловать [https://developer.mozilla.org/en-US/docs/Web/API/IDBKeyRange](https://developer.mozilla.org/en-US/docs/Web/API/IDBKeyRange).

