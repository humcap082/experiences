# ANY

左側の値を右側のサブクエリが返す集合と比較してひとつでも真なら真を返す。

少なくともひとつの行が`NULL`が比較された場合、`NULL`が返される。

`SOME`と同等。

```
sql
{<expression> | (<expression>[, ...])} <operator> ANY(<sub_query>)
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
