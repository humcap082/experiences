# LIKE

指定したパターンに一致すれば真を返します。

`SIMILAR TO`が上位互換で正規表現が使用できます。

```sql
<string> [NOT] LIKE '<pattern>' [ESCAPE]
```

## パラメータ

<details><summary>string</summary>

対象の文字列

</details>

<details><summary>pattern</summary>

ワイルカードと文字列を組み合わせて、パターンをつくる。

## 備考

<details><summary>ワイルドカード</summary>

|記号|説明|
|:---|:---|
|_|任意の一文字|
|%|0文字以上の文字列|

</details>

</details>

## 句

<details><summary>NOT</summary>

否定系にする。

```sql
NOT
```

</details>

<details><summary>ESCAPE</summary>

エスケープする文字を指定する。

```sql
ESCAPE `<escape_character>`
```

</details>
