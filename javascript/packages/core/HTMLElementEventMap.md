# HTMLElementEventMap

`HTMLElement.addEventListener()`の`type`のインタフェース

```javascript
interface HTMLElementEventMap extends ElementEventMap, GlobalEventHandlersEventMap, DocumentAndElementEventHandlersEventMap {}

interface ElementEventMap {
    "fullscreenchange": Event;
    "fullscreenerror": Event;
}

interface GlobalEventHandlersEventMap {
    "abort": UIEvent;
    "animationcancel": AnimationEvent;
    "animationend": AnimationEvent;
    "animationiteration": AnimationEvent;
    "animationstart": AnimationEvent;
    "auxclick": MouseEvent;
    "beforeinput": InputEvent;
    "blur": FocusEvent;
    "cancel": Event;
    "canplay": Event;
    "canplaythrough": Event;
    "change": Event;
    "click": MouseEvent;
    "close": Event;
    "compositionend": CompositionEvent;
    "compositionstart": CompositionEvent;
    "compositionupdate": CompositionEvent;
    "contextmenu": MouseEvent;
    "cuechange": Event;
    "dblclick": MouseEvent;
    "drag": DragEvent;
    "dragend": DragEvent;
    "dragenter": DragEvent;
    "dragexit": Event;
    "dragleave": DragEvent;
    "dragover": DragEvent;
    "dragstart": DragEvent;
    "drop": DragEvent;
    "durationchange": Event;
    "emptied": Event;
    "ended": Event;
    "error": ErrorEvent;
    "focus": FocusEvent;
    "focusin": FocusEvent;
    "focusout": FocusEvent;
    "gotpointercapture": PointerEvent;
    "input": Event;
    "invalid": Event;
    "keydown": KeyboardEvent;
    "keypress": KeyboardEvent;
    "keyup": KeyboardEvent;
    "load": Event;
    "loadeddata": Event;
    "loadedmetadata": Event;
    "loadstart": Event;
    "lostpointercapture": PointerEvent;
    "mousedown": MouseEvent;
    "mouseenter": MouseEvent;
    "mouseleave": MouseEvent;
    "mousemove": MouseEvent;
    "mouseout": MouseEvent;
    "mouseover": MouseEvent;
    "mouseup": MouseEvent;
    "pause": Event;
    "play": Event;
    "playing": Event;
    "pointercancel": PointerEvent;
    "pointerdown": PointerEvent;
    "pointerenter": PointerEvent;
    "pointerleave": PointerEvent;
    "pointermove": PointerEvent;
    "pointerout": PointerEvent;
    "pointerover": PointerEvent;
    "pointerup": PointerEvent;
    "progress": ProgressEvent;
    "ratechange": Event;
    "reset": Event;
    "resize": UIEvent;
    "scroll": Event;
    "securitypolicyviolation": SecurityPolicyViolationEvent;
    "seeked": Event;
    "seeking": Event;
    "select": Event;
    "selectionchange": Event;
    "selectstart": Event;
    "stalled": Event;
    "submit": Event;
    "suspend": Event;
    "timeupdate": Event;
    "toggle": Event;
    "touchcancel": TouchEvent;
    "touchend": TouchEvent;
    "touchmove": TouchEvent;
    "touchstart": TouchEvent;
    "transitioncancel": TransitionEvent;
    "transitionend": TransitionEvent;
    "transitionrun": TransitionEvent;
    "transitionstart": TransitionEvent;
    "volumechange": Event;
    "waiting": Event;
    "wheel": WheelEvent;
}

interface DocumentAndElementEventHandlersEventMap {
    "copy": ClipboardEvent;
    "cut": ClipboardEvent;
    "paste": ClipboardEvent;
}
```

<details><summary>click</summary>

クリックイベント

```javascript
"click": MouseEvent;
```

</details>

***

<details><summary>mouseover</summary>

マウスホバー時のイベント

```javascript
"mouseover": MouseEvent;
```

</details>

***

<details><summary>mouseout</summary>

マウスが離れたときのイベント

```javascript
"mouseout": MouseEvent;
```

</details>

***

<details><summary>load</summary>

ページや画像の読み込みが完了したときのイヴェント

```javascript
"load": Event;
```

</details>

***

<details><summary>submit</summary>

フォームを送信したときのイベント

```javascript
"submit": Event;
```

</details>

***

<details><summary>change</summary>

フィールドなどの値が変更されたときのイベント

```javascript
"change": Event;
```

</details>

***

<details><summary>focus</summary>

フィールドなどがフォーカスされたときのイベント

```javascript
"focus": FocusEvent;
```

</details>

***

<details><summary>blur</summary>

フィールドなどからフォーカスが外れた時のイベント

```javascript
"blur": FocusEvent;
```

</details>

***
