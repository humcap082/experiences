# DISTINCT

テーブルや集合の重複した行を1行にする。

```sql
DISTINCT [ON]
```

### 句

<details><summary>ON</summary>

`SELECT`中に使用でき、特定の列の重複を1行にする。

```sql
DISTINCT ON (<column_name>[,...])
```

</details>

### 例

<details><summary>集合関数の中で使用</summary>

JOINをふたつ以上結合した上で集合関数を使用すると、行が重複する可能性があるため、

集合関数のなかでDISTINCTをしようするとよい。

```sql
jsonb_agg(DISTINCT column_name);
```

</details>
