# DISTINCT

`SELECT`の中以外でもテーブルや集合の重複した行を1行にする。

```sql
DISTINCT records;
```

### 例

<details><summary>集合関数の中で使用</summary>

JOINをふたつ以上結合した上で集合関数を使用すると、行が重複する可能性があるため、

集合関数のなかでDISTINCTをしようするとよい。

```sql
jsonb_agg(DISTINCT column_name);
```
