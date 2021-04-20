# シーケンス図

2つの分類子間のメッセージを描画するために使用する。

```uml
[header]
[footer]

[title]

[skinparam]

[box]

[
    <class> {<instance> | "<instance>"} [\<\< \>\>]
    [as] [order] [#<color>]
]

[autonumber]

[create]
[<instance1>] <allow> [<instance2>] : <message>
[<note>]
[/ ...]

[<group>]

[ref over]

[\.\.\.]

[\|\|\|]  ` この行で連続する|はorを意味しない。

[activate]

[newpage]

[== ==]
```

## パラメータ

<details><summary>class</summary>

|class|説明|
|:---|:---|
|participant|参加者を表す四角のボックス(デフォルト)|
|actor|人型|
|boundary|境界を表す。|
|control|制御を表す。|
|entity|エンティティを表す。|
|database|データーベースを表す。|
|collections|集合や配列を表す。|
|queue|キューを表す。|

</details>

<details><summary>arrow</summary>

矢印

|記号|説明|
|:---|:---|
|-&gt;x|失敗|
|-&gt;|通常の矢印|
|--&gt;|点線の矢印|
|-&gt;&gt;|先端が塗りつぶされてない矢印|
|-\\ |先端が上半分の矢印|
|-\\\\ |先端が上半分で塗りつぶされてない矢印|
|-/|先端が下半分の矢印|
|-//|先端が下半分で塗りつぶされていない矢印|
|-&gt;o|先端に円がついた矢印|
|&lt;-&gt;|両端の矢印|

### 例

<details><summary>矢印に色をつける</summary>

色をつける場合は、間に`[#color]`をはさむ。

```uml
client -[#red]> server
client <-[#0000FF]- server
```

</details>

<details><summary>インとアウト</summary>

インスタンスの変わりに矢印の両端どちらかに`[`または`]`を

つけることで左端や右端に矢印をつなげられる。

```uml
@startuml
participant Alice
participant Bob #lightblue
Alice -> Bob
Bob -> Carol
...
[-> Bob
[o-> Bob
[o->o Bob
[x-> Bob
...
[<- Bob
[x<- Bob
...
Bob ->]
Bob ->o]
Bob o->o]
Bob ->x]
...
Bob <-]
Bob x<-]
@enduml
```

</details>

<details><summary>短いインとアウト</summary>

`[`ではなく`?`を使用することで跨ぐことなく、直近の余白から

インアウトの先端をつける。

```uml
@startuml
?-> Alice : ""?->""\n**short** to actor1
[-> Alice : ""[->""\n**from start** to actor1
[-> Bob : ""[->""\n**from start** to actor2
?-> Bob : ""?->""\n**short** to actor2
Alice ->] : ""->]""\nfrom actor1 **to end**
Alice ->? : ""->?""\n**short** from actor1
Alice -> Bob : ""->"" \nfrom actor1 to actor2
@enduml
```

</details>

</details>

<details><summary>note</summary>

ノートをつける

```uml
{note | hnote | rnote} {
    left of
    | right of
    | over
    | across
}
[#<color>]{: <message> | <multi_lines> end note}
```

### パラメータ

<details><summary>color</summary>
</details>

<details><summary>message</summary>
</details>

<details><summary>multi_lines</summary>
</details>

### 属性

<details><summary>note</summary>

```uml
note
```

</details>

<details><summary>hnote</summary>

```uml
hnote
```

</details>

<details><summary>rnote</summary>

```uml
rnote
```

</details>

<details><summary>left of</summary>

```uml
left of <instance>
```

</details>

<details><summary>right of</summary>

```uml
right of <instance>
```

</details>

<details><summary>over</summary>

```uml
over <instance>[, <end_instance>]
```

</details>

<details><summary>across</summary>

```uml
across
```

</details>

<details><summary>end note</summary>

```sql
end note
```

</details>

### 例

<details><summary>複数行のノート</summary>

`end note`をつける。

```uml
@startuml
Bob->Bob : I am thinking
note left
a note
can also be defined
on several lines
end note
@enduml
```

</details>

<details><summary>of/over</summary>

```uml
@startuml
participant Alice
participant Bob
note left of Alice #aqua
This is displayed
left of Alice.
end note
note right of Alice: This is displayed right of Alice.
note over Alice: This is displayed over Alice.
note over Alice, Bob #FFAAAA: This is displayed\n over Bob and Alice.
note over Bob, Alice
This is yet another
example of
a long note.
end note
@enduml
```

</details>

<details><summary>複数にまたがる</summary>

```uml
@startuml
Alice->Bob:m1
Bob->Charlie:m2
note over Alice, Charlie: Old method for note over all part. with:\n ""note over //FirstPart, LastPart//"".
note across: New method with:\n""note across""
Bob->Alice
hnote across:Note across all part.
@enduml
```

</details>

<details><summary>同じレベルに整列する。</summary>

```uml
@startuml
note over Alice : initial state of Alice
/ note over Bob : initial state of Bob
Bob -> Alice : hello
@enduml
```

</details>

</details>

<details><summary>group</summary>

グループ化する。

```uml
{alt | opt | loop | par | break | critical | group} [<message>]

<expressions>

end
```

### パラメータ

<details><summary>message</summary>
</details>

<details><summary>expressions</summary>
</details>

### 属性

<details><summary>alt</summary>

```uml
alt
```

</details>

<details><summary>opt</summary>

```uml
opt
```

</details>

<details><summary>loop</summary>

```uml
loop
```

</details>

<details><summary>par</summary>

```uml
par
```

</details>

<details><summary>break</summary>

```uml
break
```

</details>

<details><summary>critical</summary>

```uml
critical
```

</details>

<details><summary>group</summary>

```uml
group <name>
```

</details>

<details><summary>end</summary>

```uml
end
```

</details>

### 例

<details><summary>グループ化</summary>

```uml
@startuml
Alice -> Bob: Authentication Request
alt successful case
Bob -> Alice: Authentication Accepted
else some kind of failure
Bob -> Alice: Authentication Failure
group My own label
Alice -> Log : Log attack start
loop 1000 times
Alice -> Bob: DNS Attack
end
Alice -> Log : Log attack end
end
else Another type of failure
Bob -> Alice: Please repeat
end
@enduml

```

</details>

</details>

## 属性

<details><summary>&lt;&lt; &gt;&gt;</summary>

```uml
\<\< [(<a>, #<color>)] [<stereotype>] \>\>
```

インスタンスを定義時にステレオタイプを指定できる。

### 例

<details><summary>クラス名を表記する。</summary>

```uml
@startuml
participant "Famous Bob" as Bob << Generated >>
participant Alice << (C,#ADD1B2) Testable >>
Bob->Alice: First message
@enduml
```

</details>

</details>

<details><summary>as</summary>

インスタンスのエイリアスを指定する。

```uml
as <alias>
```

</details>

<details><summary>order</summary>

指定した数字で小さい順に左から並べる。

```uml
order <number>
```

</details>

<details><summary>autonumber</summary>

自動採番

```uml
autonumber [<stop> | <resume>] [<n>] [<s>] ["<format>"]
```

### 例

<details><summary>formatの使用</summary>

`Java`の`DecimalFormat`方式で指定する。

0と#が有効桁を表す。

```uml
@startuml
autonumber "<b>[000]"
Bob -> Alice : Authentication Request
Bob <- Alice : Authentication Response
autonumber 15 "<b>(<u>##</u>)"
Bob -> Alice : Another authentication Request
Bob <- Alice : Another authentication Response
autonumber 40 10 "<font color=red><b>Message 0 "
Bob -> Alice : Yet another authentication Request
Bob <- Alice : Yet another authentication Response
@enduml
```

</details>



<details><summary>stop / resumeの使用</summary>


```uml
@startuml
autonumber 10 10 "<b>[000]"
Bob -> Alice : Authentication Request
Bob <- Alice : Authentication Response
autonumber stop
Bob -> Alice : dummy
autonumber resume "<font color=red><b>Message 0 "
Bob -> Alice : Yet another authentication Request
Bob <- Alice : Yet another authentication Response
autonumber stop
Bob -> Alice : dummy
autonumber resume 1 "<font color=blue><b>Message 0 "
Bob -> Alice : Yet another authentication Request
Bob <- Alice : Yet another authentication Response
@enduml
```

</details>



</details>



<details><summary>skinparam</summary>

スキンパラメータを設定する。

```uml
skinparam <param_name> <value>
```

### 備考

<details><summary>param_name</summary>

#### パラメータ

<details><summary>responseMessageBelowArrow</summary>

シーケンス図のレスポンスのメッセージを矢印の下に配置するかどうか。

```uml
bool responseMessageBelowArrow
```

</details>



<details><summary>maxMessageSize</summary>

一行の文字数を制限し、制限を超えた場合は折り返す。

```uml
int maxMessageSize
```

</details>



<details><summary>lifelineStrategy</summary>

ライフラインのスタイル

```uml
border_style lifelineStyle
```

|border_style|説明|
|:---|:---|
|solid|実線|
|unsolid|デフォルトの点線|

</details>



</details>



</details>



<details><summary>header</summary>

ヘッダー

```uml
header <message>
```

</details>



<details><summary>footer</summary>

フッター

```uml
footer <message>
```

### 例　

<details><summary>現在のページ数を表示する。</summary>

```uml
footer Page %page% of %lastpage%
```
</details>



<details><summary>フッターの削除</summary>

`hide footbox`を記述する。

```uml
@startuml
hide footbox
title Foot Box removed
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response
@enduml
```

</details>

</details>



<details><summary>title</summary>

タイトルを設定する

```uml
title <message>
```

### 例

<details><summary>複数行</summary>

`end title`を使用する。

```uml
@startuml
title
<u>Simple</u> communication example
on <i>several</i> lines and using <font color=red>html</font>
This is hosted by <img:sourceforge.jpg>
end title
Alice -> Bob: Authentication Request
Bob -> Alice: Authentication Response
@enduml
```

</details>



</details>



<details><summary>newpage</summary>

新しいページに分割する。

```uml
newpage [<title>]
```

</details>

<details><summary>== ==</summary>

メッセージ付きの境界線

```uml
== <message> ==
```

</details>

<details><summary>ref</summary>

リファレンスを挿入する。

```uml
ref over <instance>[, <end_instance>]: {<message> | <multi_lines> end ref}
```

### パラメータ

<details><summary>instance</summary>
</details>

<details><summary>end_instance</summary>
</details>

<details><summary>message</summary>
</details>

<details><summary>multi_lines</summary>
</details>

### 属性

<details><summary>end ref</summary>

```uml
end ref
```

</details>

</details>

<details><summary>...</summary>

遅延を表現する。

```uml
[...[<message>...]]  ' この行で...は繰り返しを意味しない
```

</details>



<details><summary>&#124;&#124;&#124;</summary>

間隔を空ける。

```uml
[||| | ||<size>||]  ` この行で連続する|はorを意味しない。
```

</details>

<details><summary>activate</summary>

活性化する。

```uml
{activation <instance> [#<color>] | autoactivate on}

<expressions>

{deactivate | destroy| return}
```

### 属性

<details><summary>autoactivate on</summary>

```uml
autoacativate
```

</details>

<details><summary>deactivate</summary>

```uml
deactivate <instance>
```

</details>

<details><summary>destroy</summary>

```uml
destroy <instance>
```

</details>

<details><summary>return</summary>

```uml
return [<message>]
```

</details>

### 例

<details><summary>ネスト</summary>

```uml
@startuml
participant User
User -> A: DoWork
activate A #FFBBBB
A -> A: Internal call
activate A #DarkSalmon
A -> B: << createRequest >>
activate B
B --> A: RequestCreated
deactivate B
deactivate A
A -> User: Done
deactivate A
@enduml
```

</details>



<details><summary>returnの使用</summary>

```uml
@startuml
Bob -> Alice : hello
activate Alice
Alice -> Alice : some action
return bye
@enduml
```

</details>



<details><summary>autoactivate onの使用</summary>

```uml
@startuml
autoactivate on
alice -> bob : hello
bob -> bob : self call
bill -> bob #005500 : hello from thread 2
bob -> george ** : create
return done in thread 2
return rc
bob -> george !! : delete
return success
@enduml
```

</details>



<details><summary>ショートカット</summary>

`instance1 arrow instance2 [{** | -- | !!}[#color]]: message`で

活性化と非活性化と破棄できる。

```uml
@startuml
alice -> bob ++: hello
bob -> bob ++ #005500: self call
bob -> bob --: self complete
bob -> alice !!: failed
@enduml
```

</details>



</details>



<details><summary>create</summary>

インスタンスを作成するメッセージにする。

```uml
[create [<class>] <instance>]
```

### 例

<details><summary>ショートカット</summary>

`<instance1> <arrow> <instance2> **: <message>`で`instance2`を

作成するショートカットになる。

```uml
@startuml
bob -> george ** : create
@enduml
```


</details>



</details>



<details><summary>box</summary>

定義時にインスタンスをグループ化できる。

```uml
box <group_name> [#<color>]

<instance_definition>
[...]

end box
```

### 例

<details><summary>グループ化</summary>

```uml
@startuml
box "Internal Service" #LightBlue
participant Bob
participant Alice
end box
participant Other
Bob -> Alice : hello
Alice -> Other : hello
@enduml
```

</details>

</details>

## 備考

<details><summary>htmlとcreore</summary>

`html`や`creore`をメッセージや名前に使用できる。

### 備考

<details><summary>creore</summary>

|記号|説明|
|:---|:---|
|\*\*word\*\*|太線|
|\-\-word\-\-|打消し|
|\~\~word\~\~|波線|
|\/\/word\/\/|イタリック体|
|\"\"word\"\"|モノリシック|
|\_\_word\_\_|アンダーライン|

</details>



### 例

<details><summary>htmlとcreore</summary>

```uml
@startuml
participant Alice
participant "The **Famous** Bob" as Bob
Alice -> Bob : hello --there--
... Some ~~long delay~~ ...
Bob -> Alice : ok
note left
This is **bold**
This is //italics//
This is ""monospaced""
This is --stroked--
This is __underlined__
This is ~~waved~~
end note
Alice -> Bob : A //well formatted// message
note right of Alice
This is <back:cadetblue><size:18>displayed</size></back>
__left of__ Alice.
end note
note left of Bob
<u:red>This</u> is <color #118888>displayed</color>
**<color purple>left of</color> <s:red>Alice</strike> Bob**.
end note
@enduml
```

</details>



</details>



<details><summary>toez</summary>

`toez`プラグインを有効にすると持続時間を表示できます。

```uml
!pragma teoz true

\{start\} instance1 arrow instance2: message1
\{end\} instance2 arrow instance1: message2
\{start\} arrow \{end\}: message3
```

### 例

<details><summary>持続時間の表示</summary>

```uml
@startuml
!pragma teoz true
{start} Alice -> Bob : start doing things during duration
Bob -> Max : something
Max -> Bob : something else
{end} Bob -> Alice : finish
{start} <-> {end} : some time
@enduml
```

</details>



</details>



