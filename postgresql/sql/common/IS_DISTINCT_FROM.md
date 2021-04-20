# IS DISTINCT FROM

非NULLの入力では、IS DISTINCT FROMは<>演算子と同じです。

しかし、入力がどちらもNULLの場合、これは偽を返し、

片方の入力のみがNULLの場合は真を返します。

同様に、IS NOT DISTINCT FROMは非NULL入力では=と同じですが、

両方の入力がNULLであれば真を、片方のみがNULLの場合は偽を返します。

このように、これらの構文はNULLを"不明な値"ではなく、通常の値かのように動作します。

```sql
<expression> IS [NOT] DISTINCT FROM <expressoin>
```

## パラメータ

<details><summary>expression</summary>
</details>
