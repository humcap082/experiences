# skinparam

スキン属性を設定する。

```uml
skinparam <param_name> <value>
```

## 属性

<details><summary>&lt;param_name&gt;</summary>

### 属性

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

シーケンス図のライフラインのスタイル

```uml
border_style lifelineStyle
```

|border_style|説明|
|:---|:---|
|solid|実線|
|unsolid|デフォルトの点線|

</details>

<details><summary>classAttributeIconSize</summary>

クラス図の可視性のマークをレンダリングせず、そのまま

記号を出力する。

</details>

</details>
