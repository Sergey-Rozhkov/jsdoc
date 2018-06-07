---
description: 'https://angular.io/guide/component-styles#view-encapsulation'
---

# View encapsulation

| Emulated | `0` | Emulate `Native` scoping of styles by adding an attribute containing surrogate id to the Host Element and pre-processing the style rules provided via [styles](https://angular.io/api/core/Component#styles) or [styleUrls](https://angular.io/api/core/Component#styleUrls), and adding the new Host Element attribute to all selectors.This is the default option. |
| --- | --- | --- |
| Native | `1` | Use the native encapsulation mechanism of the renderer.For the DOM this means using [Shadow DOM](https://w3c.github.io/webcomponents/spec/shadow/) and creating a ShadowRoot for Component's Host Element. |
| None | `2` | Don't provide any template or style encapsulation. |

