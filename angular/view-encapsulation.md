---
description: 'https://angular.io/guide/component-styles#view-encapsulation'
---

# View encapsulation

| Emulated | `0` | Emulate `Native` scoping of styles by adding an attribute containing surrogate id to the Host Element and pre-processing the style rules provided via [styles](https://angular.io/api/core/Component#styles) or [styleUrls](https://angular.io/api/core/Component#styleUrls), and adding the new Host Element attribute to all selectors.This is the default option. |
| --- | --- | --- |
| Native | `1` | Use the native encapsulation mechanism of the renderer.For the DOM this means using [Shadow DOM](https://w3c.github.io/webcomponents/spec/shadow/) and creating a ShadowRoot for Component's Host Element. |
| None | `2` | Don't provide any template or style encapsulation. |

[https://blog.thoughtram.io/angular/2015/06/29/shadow-dom-strategies-in-angular2.html](https://blog.thoughtram.io/angular/2015/06/29/shadow-dom-strategies-in-angular2.html)

При создании компонента, Ангуляр помещает его в **shadowRoot**, который является частью **Shadow DOМ**. Теоретически предполагается, что мы инкапсулируем стили и данные компонентов и они не нарушают структуру страницы. К сожалению, на текущее время не все браузеры поддерживают Shadow DOМ. К счастью, Ангуляр предоставляет три варианта работы с  Shadow DOМ.

Режим работы задается с помощью **encapsulation**:

```typescript
@Component({
  moduleId: module.id,
  selector: 'my-zippy',
  templateUrl: 'my-zippy.component.html',
  styles: [` `],
  encapsulation: ViewEncapsulation.None
})
```

* **ViewEncapsulation.None** - **нет Shadow DOM**, **нет инкапсуляции стиля** и данных. Стили из каждого компонента собираются в &lt;head&gt; финального html-документа и, соответсвенно, применяются для всего документа. Другими словами, стили одного компонента могут переписать стили соседних компонентов. Также можно отметить, что все &lt;ng-content&gt; теги заменяются на &lt;script&gt; которые работают как маркеры для content insertion points.
* **ViewEncapsulation.Emulated** - **нет Shadow DOM**, **создается эмуляция** инкапсуляции данных – режим настроен по умолчанию. В этом случае стили все равно прописываются в &lt;head&gt; финального html-документа НО при каждом классе появляются уточняющие селекторы  `_ngcontent-1`, `_ngcontent-0` и `_nghost-1`. Эти селекторы служат внутренней кухней Ангуляра для уточнения точек вхождения компонентов в структуру программы. `<my-zippy title="Details" _ngcontent-0 _nghost-1>` 
  * ```markup
    </my-zippy>
      <div class="zippy" _ngcontent-1>
        <div (click)="toggle()" class="zippy__title" _ngcontent-1>
          ▾ Details
        </div>
        <div [hidden]="!visible" class="zippy__content" _ngcontent-1>
          <script type="ng/contentStart" class="ng-binding"></script>
            ...
          <script type="ng/contentEnd"></script>
        </div>
      </div>
    </my-zippy>
    ```
* **ViewEncapsulation.Native** - истинный Shadow DOM со всеми фичами и бонусами. В этом случае стили не прописываются в заголовках страницы. Вместо этого они обитают в шаблонах компонентов внутри shadow root.

