# Components

### Components

* `selector`: A CSS selector that tells Angular to create and insert an instance of this component wherever it finds the corresponding tag in template HTML. For example, if an app's HTML contains `<app-hero-list></app-hero-list>`, then Angular inserts an instance of the `HeroListComponent` view between those tags.
* `templateUrl`: The module-relative address of this component's HTML template. Alternatively, you can provide the HTML template inline, as the value of the `template` property. This template defines the component's _host view_.
* `providers`: An array of **dependency injection providers** for services that the component requires. In the example, this tells Angular that the component's constructor requires a `HeroService` instance in order to get the list of heroes to display.

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

![Data binding](../.gitbook/assets/image%20%2835%29.png)

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

