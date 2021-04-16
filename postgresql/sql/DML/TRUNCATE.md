# TRUNCATE

指定したテーブルの全ての行を素早く削除する。

```sql
TRUNCATE <name>[, ...] [CASCADE | [RESTRICT]]
```

## パラメータ

<details><summary>name</summary>

空にするテーブル名

</details>

## 句

<details><summary>CASCADE</summary>

削除対象のテーブルを参照する外部キーを持つテーブルもすべて削除する。

```sql
CASCADE
```

</details>


<details><summary>RESTRICT</summary>

削除対象のテーブルを参照する外部キーを持つテーブルが存在していて、

かつ、同時に指定されていない場合、操作を中止する。

これがデフォルトなので、省略が可能。

```sql
RESTRICT
```

</details>


