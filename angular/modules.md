# Modules

* `declarations`—The _components_, _directives_, and _pipes_ that belong to this NgModule.
* `exports`—The subset of declarations that should be visible and usable in the _component templates_ of other NgModules.
* `imports`—Other modules whose exported classes are needed by component templates declared in _this_ NgModule.
* `providers`—Creators of services that this NgModule contributes to the global collection of services; they become accessible in all parts of the app. \(You can also specify providers at the component level, which is often preferred.\)
* `bootstrap`—The main application view, called the _root component_, which hosts all other app views. Only the _root NgModule_ should set this `bootstrap` property.

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

