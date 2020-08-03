# Subject

{% embed url="https://medium.com/@luukgruijs/understanding-rxjs-behaviorsubject-replaysubject-and-asyncsubject-8cc061f1cfc0" %}

* **BehaviorSubject** имеет свойство хранить текущее значение. Это означает, что вы всегда можете напрямую получить последнее переданное значение из объекта BehaviorSubject. Можно создавать BehaviorSubjects с начальным значением.
  * `new Rx.BehaviorSubject(Math.random());`
* **ReplaySubject** сравним с BehaviorSubject тем, что он может отправлять «старые» значения новым подписчикам. Однако он обладает дополнительной характеристикой, заключающейся в том, что он может записывать часть наблюдаемого выполнения и, следовательно, сохранять несколько старых значений и «воспроизводить» их новым подписчикам. Также можно указать, как долго необходимо хранить значения.
  * `new Rx.ReplaySubject(2, 100);`
* **AsyncSubject** представляет собой вариант Subject, в котором подписчикам отправляется только последнее значение наблюдаемого выполнения, и только после завершения выполнения
