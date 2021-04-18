# UPDATE

指定したテーブルの行を更新する。

```sql
[WITH]
UPDATE <table_name> SET
[FROM]
[WHERE]
[RETURNING]
```

## パラメータ

<details><summary>table_name</summary>

更新する対象のテーブル

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

更新する対象のテーブルのエイリアスをつける。

```sql
[AS] <alias>
```

</details>

<details><summary>SET</summary>

更新する列名と値を指定する。

```sql
SET {
    <column_name> = {<expression> | DEFAULT}
    | (<column_name>[, ...]) = {<expression> | DEFAULT}
    | (<column_name>[, ...]) = (<sub_query>)
}[, ...]
```

### パラメータ

<details><summary>column_name</summary>

列名を指定する。

</details>

<details><summary>expression</summary>

更新の値をいれる。複数の列目を指定した場合は、

同じ順番で同じ数だけ値を指定する。

</details>

<details><summary>sub_query</summary>

指定した列名と同じ順番で同じかずの列を返すサブクエリ。

</details>

### 句

<details><summary>DEFAULT</summary>

デフォルトの値

```sql
DEFAULT
```

</details>

</details>

<details><summary>FROM</summary>

他のテーブルの列を参照できる。

`WHERE`で結合するときに、行が1対1になるように指定する必要がある。

```sql
FROM {<expression> [AS]}[, ...];
```

<details><summary>AS</summary>

対象のテーブルにエイリアスをつける。

省略可能。

```sql
[AS] <alias>
```

</details>

### パラメータ

</details>

<details><summary>WHERE</summary>

条件を付与する。

```sql
WHERE {<condition> | CURRENT OF}
```

### パラメータ

<details><summary>condition</summary>

真偽値を返す条件式。

</details>

### 句

<details><summary>CURRENT OF</summary>

指定したカーソルのもっとも最近の位置を指定する。

```sql
CURRENT OF <cursor_name>
```

</details>

</details>

<details><summary>RETURNING</summary>

挿入または更新した行の集合を返す。

```sql
RETURNING {<output_expression> [AS]}[,...]
```

### パラメータ

<details><summary>output_expression</summary>

任意の列名をしてする。複数指定することも可能。

全ての列を指定する場合は`*`を指定する。

</details>


### 句

<details><summary>AS</summary>

出力する列に列名をつける。省略することも可能。

```sql
[AS] <output_name>
```

</details>

</details>
