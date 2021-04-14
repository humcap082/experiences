# HTMLElement

`DOM`のインターフェース

```javascript
interface HTMLElement extends
    Element,
    DocumentAndElementEventHandlers,
    ElementCSSInlineStyle,
    ElementCSSInlineStyle,
    ElementContentEditable,
    GlobalEventHandlers,
    HTMLOrSVGElement {
```

### 属性

<details><summary>innerHTML</summary>

タグの内側

```javascript
interface InnerHTML {
    innerHTML: string;
}
```

</details>

***

<details><summary>style</summary>

タグのCSSスタイルを保持

```javascript
interface ElementCSSInlineStyle {
    readonly style: CSSStyleDeclaration;
}
```

</details>

***

### メソッド

<details><summary>addEventListener()</summary>

イベントを追加する。

```javascript
addEventListener<K extends keyof HTMLElementEventMap>(
    type: K,
    listener: (this: HTMLAnchorElement, ev: HTMLElementEventMap[K]) => any,
    options?: boolean | AddEventListenerOptions
): void;

addEventListener(
    type: string,
    listener: EventListenerOrEventListenerObject,
    options?: boolean | AddEventListenerOptions
): void;
```

</details>

***

<details><summary>removeEventListener()</summary>

イベントを除外する。

```javascript
removeEventListener<K extends keyof HTMLElementEventMap>(
    type: K,
    listener: (this: HTMLParagraphElement, ev: HTMLElementEventMap[K]) => any,
    options?: boolean | EventListenerOptions
): void;

removeEventListener(
    type: string,
    listener: EventListenerOrEventListenerObject,
    options?: boolean | EventListenerOptions
): void;
```

</details>

***
