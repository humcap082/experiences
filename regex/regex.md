# 正規表現

## 特殊文字


<details><summary>&period;</summary>

### &period;

`.`はデフォルトで改行以外の任意の文字にマッチします。

`DOTALL`フラグが指定されていれば改行も含むすべての文字にマッチします。


```
.
```

</details>

<details><summary>&circ;</summary>

### &circ;

文字列の先頭にマッチし、`MULTILINE`モードでは各改行の直後にマッチします。

```
^
```

</details>

<details><summary>&dollar;</summary>

### &dollar;

文字列の末尾、あるは文字列の末尾の改行の直前にマッチし、

`MULTILINE`モードでは各改行の直後にもマッチします。

```
$
```

</details>

<details><summary>&ast;</summary>

### &ast;

直前の正規表現を0回以上、できるだけ多く繰り返したものにマッチします。

貪欲マッチします。

```
*
```

</details>

<details><summary>&plus;</summary>

### &plus;

直前の正規表現を1回以上繰り返したものにマッチします。

貪欲マッチします。

```
+
```

</details>

<details><summary>&quest;</summary>

### &quest;

直前の正規表現を0回、または1回繰り返したものにマッチします。

貪欲マッチします。

```
?
```

</details>

<details><summary>&ast;&quest;</summary>

### &ast;&quest;

直前の正規表現を0回以上繰り返したものに非貪欲にマッチします。

```
*?
```

</details>

<details><summary>&plus;&quest;</summary>

### &plus;&quest;

直前の正規表現に1回以上繰り返したものに非貪欲にマッチします。

```
+?
```

</details>

<details><summary>&quest;&quest;</summary>

### &quest;&quest;

直前の正規表現に0回もしくは1回繰り返すものに非貪欲マッチします。

```
??
```

</details>

<details><summary>&lbrace;m&rbrace;</summary>

### &lbrace;m&rbrace;

直前の正規表現をm回数繰り返したものにマッチします。

```
{m}
```

</details>

<details><summary>&lbrace;m,n&rbrace;</summary>

### &lbrace;m,n&rbrace;

直前の正規表現をm回からn回、できるだけ多く繰り返したものにマッチします。

貪欲マッチします。`m`もしくは`n`を省略できます。

```
{m,n}
```

#### 例

<details><summary>aを3回以上</summary>

##### aを3回以上

```
a{3,}
```

</details>

</details>

<details><summary>&lbrace;m,n&rbrace;&quest;</summary>


直前の正規表現をm回からn回繰り返したものに非貪欲にマッチします。

`m`もしくは`n`を省略できます。

```
{m,n}?
```

</details>

<details><summary>&bsol;</summary>

### &bsol;

特殊文字をエスケープ、もしくは特殊シーケンスを合図します。

```
\
```

</details>

<details><summary>&lbrack;&rbrack;</summary>

### &lbrack;&rbrack;

文字の集合を指定するのに使用します。

集合の中では特殊文字は特殊な意味を失いますが、

`[`や`-`はバックスラッシュでエスケープするか、

先頭に配置する必要あります。

将来的に入れ子のサポートがされる予定で、

その場合、エスケープしなければいけなくなる記号もでてきます。

`\w`や`\S`のような文字クラスも集合のなかで受理されますが、

それにマッチする文字は`ASCII`や`LOCALE`モードが湯行であるかに依存します。

```
[]
```

#### 例

<details><summary>a, m, kのいずれかにマッチさせる。</summary>

##### a, m, kのいずれかにマッチさせる。

```
[amk]
```

</details>

<details><summary>範囲を指定する。</summary>

##### 範囲を指定する。

```
[a-z]  // あらゆる小文字とマッチする。
[0-5][0-9]  // 00から59までとマッチする。
[0-9A-Fa-f]  // 任意の16進数にマッチする。
```

</details>

</details>

<details><summary>&vert;</summary>

### &vert;

AとBを任意の正規表現として`A|B`はAとBのいずれかにマッチする表現を

作成します。この方法で複数の正規表現を`|`で区切り、分離できます。

分離された正規表現は左から右へ順に試されます。

```
|
```

</details>

<details><summary>&bsol;number</summary>

### &bsol;number

指定した番号のグループにマッチします。

```
\number
```

#### 備考

<details><summary>連続しない</summary>

'(.+)\1`は`the the`にマッチしますが`thethe`にはマッチしません。

</details>

</details>

<details><summary>&bsol;A</summary>

### &bsol;A

文字列の先頭にマッチします。

```
\A
```

</details>

<details><summary>&bsol;b</summary>

### &bsol;b

単語の先頭、もしくは末尾である空文字にマッチします。

形式的には`\w, \W`の境界線として定義されます。

`locale`モードならば、その言語の境界線として定義されます。

```
\b
```

#### 例

<details><summary>foo</summary>

`\bfoo\b`は`'foo`や`foo.`や`(foo)`、`bar foo baz`にマッチしますが、

`foobar`や`foo3`にはマッチしません。

</details>

</details>

<details><summary>&bsol;B</summary>

### &bsol;B

単語の先頭もしくは末尾でないから文字にマッチします。

```
\B
```

#### 例

<details><summary>py</summary>

`py\B`は`python`や`py3`や`py2`にはマッチしますが、

`py`、`py.`、`py!`にはマッチしません。

</details>

</details>

<details><summary>&bsol;d</summary>

### &bsol;d

`unicode`モードなら任意の10進数数字、

`ASCII`モードなら`[0-9]`と等価です。

```
\d
```

</details>

<details><summary>&bsol;D</summary>

### &bsol;d

`unicode`モードなら任意の10進数数字でない文字、

`ASCII`モードなら`[^0-9]`と等価です。

```
\D
```

</details>

<details><summary>&bsol;s</summary>

### &bsol;s

空白文字にマッチします。`[\t\n\r\f\v]`と同義です。

```

```

</details>

<details><summary>&bsol;S</summary>

### &bsol;S

空白文字でない文字にマッチします。`[^\t\n\r\f\v]`と同義です。

```
\S
```

</details>

<details><summary>&bsol;w</summary>

### &bsol;w

`Unicode`モードなら単語文字にマッチします。

`ASCII`なら`[a-zA-Z0-9_]`と同義です。

```
\w
```

</details>

<details><summary>&bsol;W</summary>

### &bsol;W

単語文字ではない任意の文字にマッチします。

`ASCII`モードなら`[^a-zA-Z0-9]`と等価です。

</details>

<details><summary>&bsol;Z</summary>

### &bsol;Z

文字列の末尾にマッチします。

```
\Z
```

</details>

## モード

<details><summary>ASCII</summary>

### ASCII

`\w, \W, \b, \B, \d, \D, \s, \S`に完全な`Unicode`マッチングではなく、

`ASCII`限定マッチングをおこないます。

</details>

<details><summary>IGNORECASE</summary>

### IGNORECASE

大文字、小文字を区別しないマッチングをおこないます。

</details>

<details><summary>LOCALE</summary>

### LOCALE

現在のロケールに合わせたマッチングをおこないます。

</details>

<details><summary>MULTILINE</summary>

### MULTILINE

`^`は文字列の銭湯で、及び各行の先頭でマッチします。

`$`は文字列の末尾、及び各行の末尾でマッチします。

</details>

<details><summary>DOTALL</summary>

### DOTALL

`.`が家業を含むあらゆる文字にマッチします。

</details>

<details><summary>VERBOSE</summary>

正規表現にコメントを加えることができ、見た目をよくできます。

これは複数行の正規表現に有効で、`#`の右側がコメントとして

無視されます。

</details>


