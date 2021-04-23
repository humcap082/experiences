# タグ

<details><summary>!DOCTYPE</summary>

html5で記述されていることを表す。ソースコードの先頭に記述する。

```html
<!DOCTYPE html>
```

</details>

<details><summary>html</summary>

htmlを包括するタグ

```html
<html>
</html>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|lang|-|言語を指定する。|

</details>

<details><summary>head</summary>

メタ情報や付加的な情報を記述する。

```html
<head>
</head>
```

</details>

<details><summary>body</summary>

画面を形成する情報を記述する。

```html
<body>
</body>
```

</details>

<details><summary>meta</summary>

メタ情報を指定するタグ。`head`タグの中に記述する。

```html
<meta>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|charset|"UTF-8"|文字コード|

### 備考

<details><summary>lang - meta</summary>

|lang|言語|
|:---|:---|
|ja|日本語|

</details>

</details>

<details><summary>title</summary>

タイトルを指定する。タブの名前になる。

```html
<title>title</title>
```

</details>

<details><summary>h(n)</summary>

見出し。`n`は`[1-6]`。数字が小さいほど、文字が大きくなる。

```html
h(n)
```

</details>

<details><summary>p</summary>

段落にする。

```html
<p>paragraph</p>
```

</details>

<details><summary>br</summary>

改行

```html
<br>
```

</details>

<details><summary>img</summary>

画像を表示する。

```html
<img>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|src|required|画像のパス|
|alt|-|画像が表示されなかった場合に表示する文字列|

</details>

<details><summary>ul</summary>

順序なしリスト。

```html
<ul>
    <li>item</li>
    [...]
</ul>
```

</details>

<details><summary>ol</summary>

順序ありリスト

```html
<ol>
    <li>item</li>
    [...]
</ol>
```

</details>

<details><summary>li</summary>

`ol`と`ul`の子となるアイテムを表すタグ

```html
<li>item</li>
```

</details>

<details><summary>dl</summary>

用語と説明をセットにして表示するリスト

```html
<dl>
    <dt>term</dt><dd>description</dd>
    [...]
</dl>
```

</details>

<details><summary>dt</summary>

`dl`のなかで用語を表す。

```html
<dt>term</dt>
```

</details>

<details><summary>dd</summary>

`dl`のなかで説明を表す。

```html
<dd>description</dd>
```

</details>

<details><summary>table</summary>

表を表示する

```html
<table>
    [<caption>caption</caption>]
    <tr>[<th>header</th>][...][<td>value</td>][...]</tr>
    [...]
</table>
```

</details>

<details><summary>caption</summary>

表の見出しをつける。

```html
<caption></caption>
```

</details>

<details><summary>tr</summary>

表の行を表示する。

```html
<tr>/[<th>header</th>][...][<td>value</td>][...]</tr>
```

</details>

<details><summary>th</summary>

`table`の列や行のヘッダ

```html
<th>header</th>
```

</details>

<details><summary>td</summary>

`table`の値を格納する

```html
<td>value</td>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|colspan|1|指定した数で列を結合|
|rowspan|1|指定した数で行を結合|

</details>

<details><summary>header</summary>

ヘッダー部分を区切る。

```html
<header></header>
```

</details>

<details><summary>article</summary>

記事の部分を区切る。

```html
<article></article>
```

</details>

<details><summary>section</summary>

章や節、項を区切る。

```html
<section></section>
```

</details>

<details><summary>footer</summary>

フッター部分を区切る。

```html
<footer></footer>
```

</details>

<details><summary>form</summary>

送信フォームを定義する。

```html
<form>
    [<input>][...]
    [<select><option></option>[...]</select>][...]
    [<textarea></textarea>][...]
</form>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|action|required|フォームの送信先|
|method|post|メソッドの指定|

</details>

<details><summary>input</summary>

フォームフィールドや送信ボタンなどを表示する。

```html
<input>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|type|text|フィールドの種類|
|name|required|フォームフィールドの名前|
|value|-|デフォルトの値の設定やラジオボックスやチェックボックスの値の設定、もしくは送信ボタン内の文字|
|checked|-|チャックボックスやラジオボックスのとき、チェック状態のときに追加する。|

### 備考

<details><summary>type</summary>

|type|説明|
|:---|:---|
|text|一行のテキストフィールド|
|email|メールアドレスのフィールド|
|password|パスワードのフィールド|
|url|urlのフィールド|
|search|検索フィールド|
|number|数値のフィールド|
|file|ファイルのフィールド|
|button|ボタン|
|radio|ラジオボタン|
|checkbox|チェックボックス|
|submit|送信ボタン|

</details>

</details>

<details><summary>textarea</summary>

複数行のテキストエリアを表示する

```html
<textarea></textarea>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|rows|-|行数|

</details>

<details><summary>select</summary>

ドロップダウンで値を設定できる。

```html
<select>
    <option>item</option>
    [...]
</select>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|name|-|フォームフィールドの名前|
|size|4|選択するとき同時に表示するアイテムの数|

</details>

<details><summary>option</summary>

`select`の子のアイテム

```html
<option>item</option>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|value|-|送信する値|

</details>

<details><summary>a</summary>

リンクを表示する。

```html
<a>alias</a>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|href|required|リンク先のurlやパスもしくはid|

</details>

<details><summary>div</summary>

ブロックとしてまとめる。

```html
<div></div>
```

</details>

<details><summary>span</summary>

インライン要素をグループ化する。`span`自身も親のインライン要素となる。

```html
<span></span>
```

</details>

<details><summary>style</summary>

`css`を埋め込められる。

```html
<style>
    css
</style>
```

</details>

<details><summary>link</summary>

スタイルシートなどの外部ファイルを取り組む。

```html
<link>
```

|属性|デフォルト|説明|
|:---|:---|:---|
|href|required|外部ファイルのパス、url|
|rel|required|ファイルの種類|

|rel|説明|
|:---|:---|
|stylesheet|cssファイル|

</details>

<details><summary>script</summary>


`javascript`を埋め込む。

```html
<script>
</script>
```
</details>
