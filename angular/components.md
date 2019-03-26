# Components

### Components

* Одним из ключевых элементов приложения являются компоненты. Компонент управляет отображением представления на экране. 
* Чтобы класс мог использоваться в других модулях, он определяется с ключевым словом export.
* Для создания компонента необходимо импортировать функцию декоратора `@Component` из библиотеки `@angular/core`. Декоратор `@Component` позволяет идентифицировать класс как компонент.
* Если бы мы не применили декоратор `@Component` к классу AppComponent, то класс AppComponent компонентом бы не считался.
* Декоратор `@Component` в качестве параметра принимает объект с конфигурацией, которая указывает фреймворку, как работать с компонентом и его представлением.



* `selector`:Селектор CSS, который сообщает Angular о создании и вставке экземпляра этого компонента везде, где он находит соответствующий тег в шаблоне HTML. Например, если HTML-код приложения содержит`<app-hero-list></app-hero-list>`, затем Angular вставляет экземпляр `HeroListComponent` представления между этими тегами.
* `templateUrl`: Модуль-относительный адрес HTML-шаблона этого компонента. Кроме того, вы можете предоставить встроенный HTML-шаблон, как значение свойства`template`. Этот шаблон определяет представление хоста компонента.
  * С помощью свойства template. Шаблон представляет кусок разметки HTML с вкраплениями кода Angular. Фактически шаблон это и есть представление, которое увидит пользователь при работе с приложением.
  * Каждый компонент должен иметь один шаблон. Однако необязательно определять шаблон напрямую с помощью свойства `template`. Можно вынести шаблон во внешний файл с разметкой html, а для его подключения использовать свойство `templateUrl`.
  * Шаблон может быть однострочным или многострочным. Если шаблон многострочный, то он заключается в косые кавычки \(\`\), которые стоит отличать от стандартных ординарных кавычек \('\).
* `providers`: Массив **dependency injection providers** для сервисов, которых требует компонент. В приведенном ниже примере это говорит Angular, что конструктор компонента требует экземпляр`HeroService`, чтобы отобразить список героев.

```typescript
@Component({
  selector:    'app-hero-list',
  templateUrl: './hero-list.component.html',
  providers:  [ HeroService ]
})
export class HeroListComponent implements OnInit {
  heroes: Hero[];
  selectedHero: Hero;

  constructor(private service: HeroService) { }

  ngOnInit() {
    this.heroes = this.service.getHeroes();
  }

  selectHero(hero: Hero) { this.selectedHero = hero; }
}
```

### Template syntax

```markup
<h2>Hero List</h2>

<p><i>Pick a hero from the list</i></p>
<ul>
  <li *ngFor="let hero of heroes" (click)="selectHero(hero)">
    {{hero.name}}
  </li>
</ul>

<app-hero-detail *ngIf="selectedHero" [hero]="selectedHero"></app-hero-detail>
```

### Data binding

```markup
<li>{{hero.name}}</li>
<app-hero-detail [hero]="selectedHero"></app-hero-detail>
<li (click)="selectHero(hero)"></li>
<input [(ngModel)]="hero.name">
```

![Data binding](../.gitbook/assets/image%20%2839%29.png)

### Pipes

```markup
{{interpolated_value | pipe_name}}
```

### Directives

#### **Structural directives**

```markup
<li *ngFor="let hero of heroes"></li>
<app-hero-detail *ngIf="selectedHero"></app-hero-detail>
```

#### **Attribute directives**

```markup
<input [(ngModel)]="hero.name">
```

```typescript
@Component({
  selector: 'my-cmp',
  template: '<div></div><span></span>'
})
class MyCmpComponent {
  public smth: string = 'some text';
}
```

```typescript
@Component({
  selector: 'my-search',
  template: `
    <input [formControl]="control">
    <div *ngFor="let item of list">{{item}}</div>
  `
})
class MyCmpComponent {
  public control: FormControl = new FormControl();
  public list: string[] = [];

  constructor(private apiService: ApiService) {
  }

  private getData(value): Observable<string[]> {
    return this.apiService.get(value);
  }
}
```

### Lifecycle Hooks

{% embed url="https://angular.io/guide/lifecycle-hooks\#peek-a-boo" %}



