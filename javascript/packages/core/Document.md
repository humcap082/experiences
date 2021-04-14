# Document

htmlファイルを直接操作するクラス。

`document`インスタンスがすでに存在する。

```
interface Document extends
    Node,
    DocumentAndElementEventHandlers,
    DocumentOrShadowRoot,
    GlobalEventHandlers,
    NonElementParentNode,
    ParentNode,
    XPathEvaluatorBase {
```

## メソッド

<details><summary>write()</summary>

htmlファイルに文字列を書き込む。

```javascript
write(...text: string[]): void;
```

</details>

***

<details><summary>querySelector()</summary>

指定した`css`セレクタに一致する最初のDOMを取得する。

```javascript
querySelector<K extends keyof HTMLElementTagNameMap>(
    selectors: K
): HTMLElementTagNameMap[K] | null;

querySelector<K extends keyof SVGElementTagNameMap>(
    selectors: K
): SVGElementTagNameMap[K] | null;

querySelector<E extends Element = Element>(selectors: string): E | null;
```
</details>

***

<details><summary>querySelectorAll()</summary>

指定した`css`セレクタに一致するDOMの配列を取得する。

```javascript
querySelectorAll<K extends keyof HTMLElementTagNameMap>(
    selectors: K
): NodeListOf<HTMLElementTagNameMap[K]>;

querySelectorAll<K extends keyof SVGElementTagNameMap>(
    selectors: K
): NodeListOf<SVGElementTagNameMap[K]>;

querySelectorAll<E extends Element = Element>(
    selectors: string
): NodeListOf<E>;
```

</details>

***
