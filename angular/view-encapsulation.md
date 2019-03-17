# View encapsulation

* [`ShadowDom`](https://angular.io/api/core/ViewEncapsulation#ShadowDom) view encapsulation uses the browser's native shadow DOM implementation \(see [Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Shadow_DOM) on the [MDN](https://developer.mozilla.org/) site\) to attach a shadow DOM to the component's host element, and then puts the component view inside that shadow DOM. The component's styles are included within the shadow DOM.
* [`Native`](https://angular.io/api/core/ViewEncapsulation#Native) view encapsulation uses a now **deprecated** version of the browser's native shadow DOM implementation - [learn about the changes](https://hayato.io/2016/shadowdomv1/).
* [`Emulated`](https://angular.io/api/core/ViewEncapsulation#Emulated) view encapsulation \(the default\) emulates the behavior of shadow DOM by preprocessing \(and renaming\) the CSS code to effectively scope the CSS to the component's view. For details, see [Appendix 1](https://angular.io/guide/component-styles#inspect-generated-css).
* [`None`](https://angular.io/api/core/ViewEncapsulation#None) means that Angular does no view encapsulation. Angular adds the CSS to the global styles. The scoping rules, isolations, and protections discussed earlier don't apply. This is essentially the same as pasting the component's styles into the HTML.

{% embed url="https://blog.thoughtram.io/angular/2015/06/29/shadow-dom-strategies-in-angular2.html" %}

{% embed url="https://angular.io/guide/component-styles\#component-styles" %}

{% embed url="https://youtu.be/qNuYwcmmOyc" %}

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

