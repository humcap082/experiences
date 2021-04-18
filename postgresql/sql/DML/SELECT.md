# SELECT

行や値を取り出す。　

```sql
SELECT
    [DISTINCT]
    <expression> [AS][, ...]
    [FROM]
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


## パラメータ

<details><summary>expression</summary>

出力する値やテーブルに出力する列。

</details>

## 句

<details><summary>WITH</summary>

メインクエリで参照可能なサブクエリを指定できる。

このサブクエリはこの文で一時テーブルとし提供され、

メインクエリで複数回使用される場合も、計算は

最初の一度のみになります。また`RETURNING`を

使用したサブクエリはここに記述する必要があります。

サブクエリは複数指定でき、

```sql
WITH {TABLE | [RECURSIVE] <with_query_name> AS}[,...]
```

### パラメータ

<details><summary>with_query_name</summary>

サブクエリの名前を指定する。

指定した名前を使ってメインクエリで参照できる。

</details>

### 句

<details><summary>TABLE</summary>

テーブルを対象とする。

```sql
TABLE <table_name>
```

</details>


<details><summary>AS</summary>

サブクエリを指定する

```sql
AS [MATERIALIZED] (<sub_query>)
```

#### パラメータ

<details><summary>sub_query</summary>

サブクエリ

##### 備考

<details><summary>自己結合</summary>

`RECURSIVE`が指定されたときに使用できる自己結合の式。

```sql
<non_recursive_term> UNION [ ALL | DISTINCT ] <recursive_term>
```

</details>

</details>

#### 句

<details><summary>MATERIALIZED</summary>

最初の一度だけ計算される。デフォルトなので、省略可能。

```sql
[NOT] MATERIALIZED
```

##### 句

<details><summary>NOT</summary>

つけることで呼ばれるたびに計算させる。

```sql
NOT
```

</details>

</details>


</details>

<details><summary>RECURSIVE</summary>

サブクエリが自己結合できるようになる。

```sql
RECURSIVE
```

</details>

</details>

<details><summary>AS</summary>

出力するテーブルの列に列名を指定する。

省略することも可能。

```
[AS] <output_name>
```

</details>

<details><summary>DISTINCT</summary>

重複した行を1行にする。

```sql
DISTINCT [ON]
```

### 句

<details><summary>ON</summary>

特定の列の重複を1行にする。

```sql
ON (<column_name>[,...])
```

</details> 

</details>

<details><summary>FROM</summary>

列を取り出す対象のテーブルや集合を指定する。

```sql
FROM {<expression> [AS] [JOIN]}[, ...];
```

### 句

<details><summary>AS</summary>

対象のテーブルにエイリアスをつける。

省略可能。

```sql
[AS] <alias>
```

</details>

<details><summary>JOIN</summary>

テーブルや集合の結合

```sql
{[NATURAL] {CROSS | [INNER] | {LEFT | RIGHT | FULL}}
    JOIN <from_item> [AS]
    {ON | USING}[...]
```

#### パラメータ

<details><summary>from_item</summary>

結合するテーブルや集合

</details>

#### 句

<details><summary>INNER</summary>

内部結合を表す。省略可能

片方に存在しない行は省かれます。

```sql
[INNER]
```

</details>


<details><summary>LEFT</summary>

左外部結合

左のテーブルの行に右のテーブルの行が存在しない場合、

右のテーブルの行がNULLで補完され結合します。

その逆は省かれます

```sql
LEFT [OUTER]
```



##### 句

<details><summary>OUTER</summary>

外部結合を表す。(省略可能だが手前にLEFTまたはRIGHTまたはFULLをつける)

```sql
[OUTER]
```

</details>



</details>

<details><summary>RIGHT</summary>

右外部結合

右のテーブルの行に左のテーブルの行が存在しない場合、

左のテーブルの行がNULLで補完され結合します。

その逆は省かれます。

```sql
RIGHT [OUTER]

```

##### 句

<details><summary>OUTER</summary>

外部結合を表す。(省略可能だが手前にLEFTまたはRIGHTまたはFULLをつける)

```sql
[OUTER]
```

</details>

</details>

<details><summary>FULL</summary>


完全外部結合

どちらかに存在しない行はNULLで補完され結合します。

```sql
FULL [OUTER] JOIN table_name ON (boolean_expression);
```

##### 句

<details><summary>OUTER</summary>

外部結合を表す。(省略可能だが手前にLEFTまたはRIGHTまたはFULLをつける)

```sql
[OUTER]
```

</details>

</details>

<details><summary>CROSS</summary>

直積する。これは`INNER JOIN table ON TRUE`と同じ。

```sql
CROSS
```

</details>

<details><summary>ON</summary>

結合条件を記述

```sql
ON (<join_condition>)
```

#### パラメータ

<details><summary>join_condition</summary>

結合する条件式を記述。

</details>

</details>

<details><summary>USING</summary>

指定した列名と同じ列名の列で結合する。

```sql
USING (<column_name>[, ...])
```

</details>

<details><summary>NATURAL</summary>

結合する表の同じ名前同士で結合する。

同じ名前が存在しない場合、`ON TRUE`と同じ。

```sql
NATURAL
```

</details>

#### 例

<details><summary>二つ以上の結合</summary>

JOINをふたつ以上結合した上で集合関数を使用すると、行が重複する可能性があるため、

集合関数のなかでDISTINCTをしようするとよい。

```sql
SELECT
    jsonb_agg(DISTINCT t2.a), jsonb_agg(t3. a);
    FROM t1 NATURAL JOIN t2 NATURAL JOIN T3;
```

</details>

</details>

</details>

<details><summary>WHERE</summary>

条件を指定する。

```sql
WHERE <condition>
```

### パラメータ

<details><summary>condition</summary>

真偽値を返す任意の式

</details>

</details>

<details><summary>GROUP BY</summary>

集計関数などを使用する時に対象となる列を選ぶ、対象となった列は

その列ごとに集計関数が呼び出される。

```sql
GROUP BY <grouping_element>[, ...]
```

### 備考

<details><summary>射影</summary>

集計関数の値と列の値を同時に

射影する場合は射影する列の値もGROUP BYに指定する必要がある。

</details>

</details>

<details><summary>HAVING</summary>

`WHERE`がグループ化される前の個々のデータに対してフィルタをかけるのに対し、

`HAVING`は`GROUP BY`でグループされたあとの個々のグループにフィルタをかける。

集約関数などを使用した条件式はここに記述する。`GROUP BY`が存在しない

場合でもすべての行を1つのグループとしてみなされる。

```sql
HAVING condition
```

### パラメータ

<details><summary>condition</summary>

真偽値を返す条件式。集約関数を含められる。

</details>

</details>

<details><summary>UNION</summary>

指定した`SELECT`文との和集合になります。

指定する文の結果の列と型は同じである必要がある。

```sql
UNION [ALL | [DISTINCT]] <select_statement>
```

### パラメータ### 

<details><summary>select_statement</summary>

`ORDER BY, LIMIT, FOR NO KEY UPDATE, FOR UPDATE, FOR SHARE, FOR KEY SHARE`

を持たない任意の`SELECT`文が入る。`()`で囲んでサブクエリとして渡せば、

`ORDER BY`と`LIMIT`は使用できます。

</details>

### 句

<details><summary>ALL</summary>

重複を無視してすべての行を表示するので、

`DISTINCT`よりは高速

```sql
ALL
```

</details>

<details><summary>DISTINCT</summary>

重複を削除します。

デフォルト値なので、省略が可能。

```sql
DISTINCT
```

</details>

</details>

<details><summary>INTERSECT</summary>

指定した`SELECT`文との積集合になる。

指定する文の結果の列と型は同じである必要がある。

```sql
INTERSECT [ALL | [DISTINCT]] select_statement
```

### パラメータ

<details><summary>select_statement</summary>

`ORDER BY, LIMIT, FOR NO KEY UPDATE, FOR UPDATE, FOR SHARE, FOR KEY SHARE`

を持たない任意の`SELECT`文が入る。`()`で囲んでサブクエリとして渡せば、

`ORDER BY`と`LIMIT`は使用できます。

</details>

### 句

<details><summary>ALL</summary>

左側テーブルにm個、右側テーブルにn個の重複がある行は、

min(m,n)個出現します。

```sql
ALL
```

</details>

<details><summary>DISTINCT</summary>

重複を削除します。

デフォルト値なので、省略が可能。

```sql
DISTINCT
```

</details>



</details>

<details><summary>EXCEPT</summary>

指定した`SELECT`文との差集合になります。

指定する文の結果の列と型は同じである必要がある。

```sql
EXCEPT [ALL | [DISTINCT]] <select_statement>
```

### パラメータ

<details><summary>select_statement</summary>

`ORDER BY, LIMIT, FOR NO KEY UPDATE, FOR UPDATE, FOR SHARE, FOR KEY SHARE`

を持たない任意の`SELECT`文が入る。`()`で囲んでサブクエリとして渡せば、

`ORDER BY`と`LIMIT`は使用できます。

</details>

### 句

<details><summary>ALL</summary>

左側テーブルにm個、右側テーブルにn個の重複がある行は、

min(m - n, 0)個出現します。

```sql
ALL
```

</details>

<details><summary>DISTINCT</summary>

重複を削除します。

デフォルト値なので、省略が可能。

```sql
DISTINCT
```

</details>

</details>

<details><summary>ORDER BY</summary>

指定した式にしたがってソートする。

```sql
ORDER BY <expression> [[[ASC] | DESC | USING] [NULLS]][, ...]]
```

### パラメータ

<details><summary>expression</summary>

出力列の名前、または序数、あるいは入力列値から形成される任意の式

</details>

### 句

<details><summary>ASC</summary>

昇順にする。デフォルトなので省略が可能。

```sql
ASC
```

</details>

<details><summary>DESC</summary>

降順にする。

```sql
DESC
```

</details>

<details><summary>USING</summary>

記号で昇順、降順を指定する。

```sql
USING {< | >}
```

</details>

<details><summary>NULLS</summary>

`NULL`の値を最初にもってくるか、後ろに持ってくるかを指定する。

指定されてない場合、`ASC`のときは最後、`DESC`が指定された時は、

最初にきます。

```sql
NULLS {FIRST | LAST}
```

#### 句


<details><summary>FIRST</summary>

最初に`NULL`をもってくる。

```sql
FIRST
```

</details>

<details><summary>LAST</summary>

最後に`NULL`をもってくる。

```sql
LAST
```

</details>

</details>

</details>

<details><summary>LIMIT</summary>

返される行の最大値を指定する。

`ORDER BY`と併用することが推奨される。

```sql
LIMIT {<count> | ALL}
```

### パラメータ

<details><summary>count</summary>

行の最大値。`NULL`が渡された時は制限なし。

</details>

### 句

<details><summary>ALL</summary>

制限なし

```sql
ALL
```

</details>

</details>

<details><summary>OFFSET</summary>

 指定した行数分、とばされる。

```sql
OFFSET <start>
```

### パラメータ

<details><summary>start</summary>

とばす行数

</details>

</details>
