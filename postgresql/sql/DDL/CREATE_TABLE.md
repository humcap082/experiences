# CREATE TABLE

新しいテーブルを作成する。

```sql
CREATE [TEMP | UNLOGGED] TABLE [IF NOT EXISTS] <table_name> [PARTITION | OF] [(
    {
        {
            <column_name> {<data_type> | WITH OPTIONS} [COLLATE]
                [CONSTRAINT] [NULL] [CHECK] [DEFAULT] [GENERATED]
                [UNIQUE] [PRIMARY KEY] [REFERENCES] [DEFERRABLE]
                [INITIALLY]
        }
        [, ...]
        [, CONSTRAINT]
        [, CHECK]
        [, UNIQUE]
        [, PRIMARY KEY]
        [, EXCLUDE]
        [, FOREIGN KEY]
        [, DEFERRABLE]
        [, INITIALLY]
        | LIKE
    }
)] [FOR VALUES]
[INHERITS]
[PARTITION BY]
[USING]
[WITH | WITHOUT OIDS]
[ON COMMIT]
[TABLESPACE]
```

## パラメータ

<details><summary>table_name</summary>

作成するテーブル名

</details>

<details><summary>column_name</summary>

テーブルに作成する列名

</details>

<details><summary>data_type</summary>

列のデータ型

</details>

## 句

<details><summary>TEMP</summary>

一時テーブルとする。`TEMPORARY`でもよい。

一時テーブルは現在のセッションやトランザクションの終わりに自動的に削除される。

一時テーブルのインデックスも一時的なものになります。

既に存在するテーブル名と被った場合は、一時テーブルが優先して参照されます。

```TEMP
TEMP
```

</details>

<details><summary>UNLOGGED</summary>

ログをとらないテーブルとする。

ログをとらないため、相当高速になるが、クラッシュ時に安全ではなくなる。

```sql
UNLOGGED
```

</details>

<details><summary>IF NOT EXISTS</summary>

同じ名前のテーブルが存在していてもエラーになりません。

かわりに注意が発せられます。

```sql
IF NOT EXISTS
```

</details>

<details><summary>COLLATE</summary>

文字列の比較やソートの照合順を指定します。`text, varchar, char`などの文字列の列に定義できます。

デフォルトは`"default`でそのローカルの言語に依存します。

```sql
COLLATE "<collation>"
```

<details><summary>collation</summary>

照合順序

|照合順序|説明|
|:---|:---|
|default|ローカルの言語に依存|
|C|ASCIIに準拠|
|POSIX|ASCIIに準拠|
|ucs_basic|Unicodeに準拠|

</details>

</details>

<details><summary>CONSTRAINT</summary>

列制約、テーブル制約の名前。列や、テーブルにかけられた制約に名前を指定できる。

列名の直後に記述すると、その列の制約名になり、列のリストの一つとして記述した場合は

そのテーブルの制約名になる。

```sql
CONSTRAINT <constraint_name>
```

</details>

<details><summary>NULL</summary>

その列が`NULL`をもてることを指定する。これがデフォルト。


```sql
[NOT] NULL
```

### 句

<details><summary>NOT</summary>

その列が`NULL`をもてないことを指定する。

</details>

</details>

<details><summary>CHECK</summary>

検査制約を指定する。

新しい行、または行が更新された時に満たす必要がある条件を記述します。

`TRUE`と`UNKNOWN`と評価される式は成功します。列制約として指定された

検査制約はその列のみを参照できます。テーブル制約として指定された検査制約は

複数の列を参照できます。現在、他の列、変数は検査制約では使用できません。

```sql
CHECK (<expression>) [NO INHERIT]
```

### パラメータ

<details><summary>expression</summary>

真偽値を返す条件を記述します。列制約の場合は、その列のみを参照でき、

テーブル制約として指定された場合は、そのテーブルの列を参照できる。

</details>

### 句

<details><summary>NO INHERIT</summary>

この句を含む場合、子テーブルには制約が伝搬しない。

```sql
NO INHERIT
```

</details>

</details>

<details><summary>DEFAULT</summary>

その列にデフォルトの値が割り当てられる。値が設定されなかった場合に

指定された値がデフォルトではいる。この句を指定しなかった場合、

デフォルトは`NULL`。

```sql
DEFAULT <default_expr>
```

### パラメータ

<details><summary>default_expr</summary>

デフォルトになる値。変数は含められず、サブクエリも、他の列の値も

含めることもできない。

</details>

</details>

<details><summary>GENERATED</summary>

ユーザーは列の値を指定できず、自動的に値を生成する列になる。

```sql
GENERATED {
    ALWAYS AS (<generation_expr>) STORED 
    | {ALWAYS | BY DEFAULT} AS IDENTITY
}
```

### パラメータ

<details><summary>generation_expr</summary>

自動的に生成する値の式。そのテーブルの他の列を参照することができます。

使用される演算子や関数はイミュータブルでなければなりません。

</details>

### 句

<details><summary>ALWAYS</summary>

行を挿入時に`INSERT`に`OVERRIDING SYSTEM VALUE`を指定しないと、

上書きすることができない。

```sql
ALWAYS
```

</details>

<details><summary>BY DEFAULT</summary>

行を挿入時に`INSERT`に`OVERRIDING USER VALUE`を指定しないと

上書きをすることができない。

```sql
BY DEFAULT
```

</details>

<details><summary>IDENTITY</summary>

シーケンスと暗示的に紐づけられ、シーケンスからとられた値が自動的にはいる。

```sql
IDENTITY [(
    [AS] [INCREMENT] [MINVALUE] [MAXVALUE]
        [START] [CACHE] [CYCLE] [OWNED BY]
)]
```

</details>

</details>

<details><summary>UNIQUE</summary>

一意性制約を設ける。一意性制約では`NULL`値は等しいとみなされません。

一意性制約を設けると`btree`インデックスが自動的に作成されます。

複数の列をセットで一意とみなす場合はテーブル制約を使用します。

```sql
UNIQUE -- 列制約
UNIQUE (<column_name>[, ...]) [INCLUDE] -- テーブル制約
```

### 句

<details><summary>INCLUDE</summary>

一意でない列を明示的に指定することができる。

```sql
INCLUDE (<column_name>[, ...])
```

</details>

</details>

<details><summary>PRIMARY KEY</summary>

主キー制約を設ける。主キー制約は一意であり、非`NULL`である必要があり、

1つのテーブルに1つだけ指定できます。

主キーには`bree`インデックスが自動的に作成されます。

```sql
PRIMARY KEY  -- 列制約
PRIMARY KEY (<column_name>[, ...]) [INCLUDE] -- 表制約
```

### 句

<details><summary>INCLUDE</summary>

一意でない列を明示的に指定することができる。

```sql
INCLUDE (<column_name>[, ...])
```

</details>

</details>

<details><summary>REFERENCES</summary>

外部キー制約を設ける。

```sql
REFERENCES <ref_table> [(<ref_column>)] [MATCH] [ON DELETE] [ON UPDATE]
```

### パラメータ

### 句

</details>
