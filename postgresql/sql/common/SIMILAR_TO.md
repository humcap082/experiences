# SIMILAR TO

`LIKE`の上位互換で、正規表現にマッチしたとき真を返す。

```sql
<string> [NOT] SIMILAR TO '<pattern>' [ESCAPE]
```

## パラメータ

<details><summary>string</summary>

対象の文字列

</details>

<details><summary>pattern</summary>

正規表現

</details>

## 句

<details><summary>NOT</summary>

否定系

```sql
NOT
```

</details>

<details><summary>ESCAPE</summary>

エスケープする文字を指定。

```sql
ESCAPE <escape_character>
```

</details>
