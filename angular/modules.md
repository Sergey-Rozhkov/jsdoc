# Modules

NgModule представляет функцию-декоратора, которая принимает объект, свойства которого описывают метаданные модуля. Наиболее важные свойства:

* **declarations**: Классы представлений \(view classes\), которые принадлежат модулю. Angular имеет три типа классов представлений: компоненты \(components\), директивы \(directives\), каналы \(pipes\).
* **exports**: Набор классов представлений, которые должны быть видимы и использоваться в шаблонах компонентов из других модулей.
* **imports**: Другие модули, классы которых необходимы для шаблонов компонентов из текущего модуля.
* **providers**: Классы, создающие сервисы, которые этот NgModule вносит в глобальный набор услуг. Они становятся доступными во всех частях приложения. \(Вы также можете указать providers на уровне компонентов, что часто является предпочтительным.\)
* **bootstrap**: The main application view. Корневой компонент, который вызывается по умолчанию при загрузке приложения. Только корневой NgModule должен установить bootstrap.

```typescript
import { NgModule }      from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
@NgModule({
  imports:      [ BrowserModule ],
  providers:    [ Logger ],
  declarations: [ AppComponent ],
  exports:      [ AppComponent ],
  bootstrap:    [ AppComponent ]
})
export class AppModule { }
```

