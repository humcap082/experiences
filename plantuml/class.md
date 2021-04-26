# クラス図

クラス間の関係を表す図。

```uml
@startuml
[<class>]
<arrow>
[<class_name> :]
@enduml
```

## パラメータ

<details><summary>&lt;class&gt;</summary>

### &lt;class&gt;

クラスの定義

|class|説明|
|:---|:---|
|abstract|抽象クラス|
|annotation|注釈|
|circle|円|
|()|小さい円|
|class|一般的なクラス|
|diamond|ひし形|
|&lt;&gt;|小さいひし形|
|enum|列挙型|
|entity|実態|
|interface|インタフェース|

```puml
<class> <class_name> [\{
    [<visibility>] [\{<category>\}] <type> {<field> | <method>()}
    [...]
    [..]  ' ここで..は繰り返しを示さない。
    [==]
\}]
```

#### 属性

<details><summary>&lt;visibility&gt;</summary>

##### &lt;visibility&gt;

|visibility||
|:---|:---|
|-|private|
|#|protected|
|~|package private|
|+|public|

```puml
<visibility>
```

</details>

<details><summary>&lt;category&gt;</summary>

##### &lt;category&gt;

明示的に次を指定できます。

|category|説明|
|:---|:---|
|field|フィールド|
|method|メソッド|
|static|静的|
|abstract|抽象|

```puml
<category>
```

</details>

<details><summary>..</summary>

##### ..

点線で区切る。

```puml
..[<message>..]
```

</details>

<details><summary>==</summary>

##### ==

二重線で区切る

```puml
==[<message>==]
```

</details>

</details>

<details><summary>&lt;arrow&gt;</summary>

### &lt;arrow&gt;

クラスの関係

`--`の代わりに`..`で点線になる。

|arrow|説明|
|:---|:---|
|&lt;&#124;--|継承|
|*--|構成|
|o--|集約|
|&lt--||
|#--||
|x--||
|}--||
|+--||
|^--||

```puml
<class_name> ["<message1>"] <arrow> ["message2"] <class_name> : [\<] <message3> [\>]
```

</details>

<details><summary>&lt;class_name&gt; :</summary>

```puml
<class_name> : {[type] <method>() | [<type>] <field>}
```

</details>
