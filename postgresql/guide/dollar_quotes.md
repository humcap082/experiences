# ドル引用符

ドル引用符というものがあり、'name'とおなじ文字列定数を表すが、

中の文字がエスケープされるのでバックスラッシュやシングルクォート、その他の特殊文字を

通常の文字列として解釈します。

```sql
$[<tag>]$<documents>$[<tag>]$
```

## 備考

<details><summary>tag</summary>

`tag`の位置にキーワードを付与することで、そのキーワードはエスケープされません。

</details>

## 例

<details><summary>関数に使用される例</summary>

```sql
CREATE FUNCTION func() AS
$func$
expression
$func$
```

</details>