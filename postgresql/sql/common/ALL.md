# ALL

左側の値を右側のサブクエリが返す集合と比較してすべて真なら真を返す。

ひとつでも`NULL`が比較された場合は`NULL`が返される。

```
sql
{<expression> | (<expression>[, ...])} <operator> ALL(<sub_query>)
```

## パラメータ

<details><summary>expression</summary>

比較される値。複数指定される場合は、括弧でくくり、

右側のサブクエリの列も同じ数だけ返さなければならない。

</details>

<details><summary>operator</summary>

比較演算子を渡す。

</details>

<details><summary>sub_query</summary>

サブクエリ。

</details>
