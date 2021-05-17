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
