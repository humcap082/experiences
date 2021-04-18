# IN

指定した値が、指定したリストや集合に存在するか真偽値を返す。

左側の式もしくは、右側の式どちらかがひとつでも`NULL`を持つ場合は`NULL`が返される。

```sql
{expression | (<expression>[, ...])} [NOT] IN ({<sub_query> | <value>[, ...]})
```

## パラメータ

<details><summary>expression</summary>

存在を確認したい値。

複数指定する場合は、括弧でくくり、

右側の式はサブクエリである必要があり、

そのサブクエリは同じ数の列を返さなければなりません。

</details>

<details><summary>sub_query</summary>

サブクエリ

</details>

<details><summary>value</summary>

値

</details>

## 句

<details><summary>NOT</summary>

否定系

```sql
NOT
```

</details>

