# NULLIF()

2つの引数が等しい時、NULLをかえし、異なる場合は、第一引数を返す。

```sql
NULLIF(<value1>, <value2>)
```

## 例

<details><summary>[null] -> null</summary>

```sql
NULLIF(jsonb_agg(column_or_null), '[null]');
```

</details>
