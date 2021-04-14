# CSSプロパティ

<details><summary>color</summary>

色

```css
color: clr;
```

</details>

***

<details><summary>font-size</summary>

フォントサイズ

```css
font-size: size;
```

</details>

***

<details><summary>width</summary>

幅

```css
width: size;
```

</details>

***

<details><summary>height</summary>

高さ

```css
height: size;
```

</details>

***

<details><summary>margin</summary>

余白

```css
margin: {
    all
    | top right bottom left
    | vertical horizontal
    | top horizontal bottom
    | inherit
    | initial
    | unset
};
```

</details>

***

<details><summary>padding</summary>

パディング

```css
padding: {
    all
    | top right bottom left
    | vertical horizontal
    | top horizontal bottom
};
```

</details>

***

<details><summary>border</summary>

罫線のスタイルを指定する。　

```css
border: size color border_style;
```

#### 備考

<details><summary>border_style</summary>

|style|説明|
|:---|:---|
|none|表示しない。重なる場合は、ほかの要素を有線。|
|hidden|表示しない。重なる場合は、そのボーダーも表示しない。|
|solid|1本線|
|double|2本線|
|groove|立体的にくぼんだ線|
|ridge|立体的に隆起した線|
|inset|中身がくぼんだ線|
|outset|中身が隆起した線|
|dashed|破線|
|dotted|点線|

</details>

***

</details>

***

<details><summary>font-size</summary>

フォントサイズを指定する。

```css
font-size: size;
```

</details>

***

<details><summary>font-style</summary>

フォントのスタイルを指定する。

```css
font-style: {normal | italic};
```

</details>

***

<details><summary>text-decoration</summary>

テキストにデコレーションする。

```css
text-decoration: {underline | overline | line-through};
```

</details>

***

<details><summary>text-align</summary>

行寄せ

```css
text-align {
    start
    | end
    | left
    | right
    | center
    | justify
    | justify-all 
     match_parent
};
```

#### 備考

<details><summary>alignments</summary>

|alignments|説明|
|:---|:---|
|start|デフォルト、行方向の最初にそろえる。|
|end|行方向の最後にそろえる。|
|left|左にそろえる。|
|right|右にそろえる|
|center|中央にそろえる。|
|justify|均等にそろえる。|
|justify-all|均等にそろえる。最後の行もそろえる。|
|match-parent|親要素を継承する。|

</details>

***

</details>

***

<details><summary>text-indent</summary>

文字のインデントサイズ

```css
text-indent: size;
```

</details>

***

<details><summary>line-height</summary>

行の高さ

```css
line-height: size;
```

</details>

***

<details><summary>float</summary>

配置変更。

後に続くタグはその反対側に続く。

`position`プロパティで`static`以外が指定されている要素には適用されない。

```css
float: {left | right | none};
```

</details>

***

<details><summary>display</summary>

表示形式を変更できる。

```css
display: {block | inline | inline-block | flex};
```

#### 備考

<details><summary>表示形式</summary>

|format|説明|
|:---|:---|
|block|ブロック|
|inline|インライン|
|inline-block|ブロックレベルの要素をインラインのように扱い横に並べる。|
|flex|子を横に並べる。|

</details>

***

</details>

***

<details><summary>background</summary>


```css
background {
    color
    | url repeat_style
    | border-box color
    | repeat_style alignment/size% url
};
```


</details>

***

<details><summary>background-color</summary>

背景色

```css
background-color: color;
```

</details>

***

<details><summary>background-image</summary>

背景画像。

```css
background-image: url;
```

</details>

***

<details><summary>background-repeat</summary>

背景画像の繰り返しを設定する。

```css
background-repeat: {repeat-x | repeat-y | repeat | no-repeat};
```

</details>

***

<details><summary>background-position</summary>

背景画像の表示位置を設定する。

```css
background-position: {{top | left | right | center} [margin]}[...];
```

</details>

***

<details><summary>list-style-position</summary>

リストの先頭に表示するマーカーの表示位置を指定する。

```css
list-style-position: {inside | outside};
```

#### 備考

<details><summary>position</summary>

|position|説明|
|:---|:---|
|inside|マーカーがリスト内容の内側に表示される。改行時にマーカーと行頭がそろう。|
|outside|マーカーがリスト内容の外側に表示される。改行時に文字がマーカーの手前にくる。|

</details>

***

</details>

***

<details><summary>cursor</summary>

ホバー時のカーソルの形を変更する。

```css
cursor shape;
```

#### 備考

<details><summary>shape</summary>

|shape|説明|
|:---|:---|
|auto|自動|
|default|デフォルトカーソル|
|none|表示しない|
|pointer|指のマーク|
|help|クエスチョンマーク付き|
|progress|読み込み中|
|wait|待機中|
|cell|表のセルまたは一連のセルの選択|
|crossshair|十字カーソル|
|text|テキスト入力|
|vertical-text|縦書き入力|
|alias|ショットカット作成|
|copy|コピー|
|move|移動|
|no-drop|ドロップできない|
|not-allowed|禁止マーク|
|grab|つかむ前|
|grabbing|つかんでいる|

</details>

***

</details>

***

## 備考


<details><summary>サイズの単位</summary>

|単位|説明|
|:---|:---|
|(n)em|親要素のフォントサイズを1とする|
|(n)rem|html要素のフォントサイズを1とする|
|(n)%|親要素との相対的な大きさ|
|(n)px|ピクセル|
|auto|自動|

</details>

***

<details><summary>repeat_style - background-repeat, background</summary>

|repeat_style|説明|
|:---|:---|
|repeat-x|横に繰り返す。|
|repeat-y|縦に繰り返す。|
|repeat|縦横に繰り返す。|
|no-repeat|繰り返しなし。|

</details>

***
