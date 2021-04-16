# SELECT

行や値を取り出す。　

```sql
SELECT [DISTINCT [ON] (column_name[, ...])] [expression][, ...] [FROM expression]
    [JOIN]
    [WHERE]
    [GROUP BY]
    [HAVING]
    [{UNION | INTERSECT | EXCEPT}]
    [ORDER BY]
    [LIMIT]
    [OFFSET]
    [FETCH]
    [FOR]
```
<dl>

<dt><h2>句</h2></dt>

<dd><details><summary>DISTINCT</summary>

重複した行を1行にする。

```sql
DISTINCT [ON (column_name[,...])]
```
<dl>

<dt><h3>句</h3></dt>

<dd><details><summary>ON</summary>

特定の列の重複を1行にする。

```sql
DISTINCT ON (column_name[,...])
```

</details></dd>

</dl>

</details></dd>

<dd><details><summary>FROM</summary>

列を取り出す対象のテーブルや集合を指定する。

```sql
FROM table_name [AS alias];
```

</details></dd>

<dd><details><summary>JOIN</summary>

テーブルの結合

```sql
{{[INNER] | {LEFT | RIGHT | FULL} [OUTER]} JOIN table_name
    ON (boolean_expression)}[...]
```

<dl>

<dt><h3>句</h3></dt>

<dd><details><summary>INNER</summary>

デフォルトであり、内部結合を表す。

片方に存在しない行は省かれます。

```sql
INNER JOIN table_name ON (boolean_expression);
```

</details></dd>

<dd><details><summary>OUTER</summary>

外部結合を表す。(省略可能だが手前にLEFTまたはRIGHTまたはFULLをつける)

```sql
{LEFT | RIGHT | FULL} [OUTER] JOIN table_name ON (boolean_expression);
```

</details></dd>

<dd><details><summary>LEFT</summary>

左外部結合

左のテーブルの行に右のテーブルの行が存在しない場合、

右のテーブルの行がNULLで補完され結合します。

その逆は省かれます

```sql
LEFT [OUTER] JOIN table_name ON (boolean_expression);
```

</details></dd>

<dd><details><summary>RIGHT</summary>

右外部結合

右のテーブルの行に左のテーブルの行が存在しない場合、

左のテーブルの行がNULLで補完され結合します。

その逆は省かれます。

```sql
RIGHT [OUTER] JOIN table_name ON (boolean_expression);
```

</details></dd>


<dd><details><summary>FULL</summary>


完全外部結合

どちらかに存在しない行はNULLで補完され結合します。

```sql
FULL [OUTER] JOIN table_name ON (boolean_expression);
```

</details></dd>

<dt><h3>例</h3></dt>

<dd><details><summary>二つ以上の結合</summary>

JOINをふたつ以上結合した上で集合関数を使用すると、行が重複する可能性があるため、

集合関数のなかでDISTINCTをしようするとよい。

```sql
jsonb_agg(DISTINCT column_name);
```

</details></dd>

</dl>

</details></dd>

<dd><details><summary>GROUP BY</summary>

集計関数などを使用する時に対象となる列を選ぶ、対象となった列は

その列ごとに集計関数が呼び出される。

```sql
GROUP BY column_name[,...]
```

<dl>

<dt><h3>備考</h3></dt>

<dd><details><summary>射影</summary>

集計関数の値と列の値を同時に

射影する場合は射影する列の値もGROUP BYに指定する必要がある。

</details></dd>

<dd><details><summary>集計関数を用いた条件式</summary>

集計関数を使用した条件はHAVINGに指定する。

</details></dd>

</dl>

</details></dd>

</dl>