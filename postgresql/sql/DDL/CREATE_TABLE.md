# CREATE TABLE

新しいテーブルを作成する。

```sql
CREATE [TEMP | UNLOGGED] TABLE [IF NOT EXISTS] <table_name> {
    ({
        {
            <column_name> <data_type> [COLLATE]
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
    })
    | AS
    | OF
    | PARTITION OF
}
[INHERITS]
[PARTITION BY]
[USING]
[WITH]
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

デフォルトは`"default`でデータベースの`lc_collate`に依存します。

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

外部キー制約を設ける。一時テーブルとの間に外部キー制約を設けることはできない。

```sql
REFERENCES <ref_table> [(<ref_column>)] [MATCH] [ON DELETE] [ON UPDATE]
```

### パラメータ

<details><summary>ref_table</summary>

被参照テーブル。

</details>

<details><summary>ref_column</summary>

被参照列。省略した場合は、被参照テーブルの主キーになる。

被参照列は主キー制約もしくは一意性制約が設けられてる必要があります。

</details>

### 句

<details><summary>MATCH</summary>

照合型を指定する。

```MATCH
MATCH {FULL | PARTIAL | SIMPLE}
```

#### 句

<details><summary>FULL</summary>

複数、外部キーがあるとき、一部が`NULL`であることを許可しない。

全ての外部キーが`NULL`であるときは、被参照テーブルを参照できないものとして

許可される。

```sql
FULL
```

</details>

<details><summary>SIMPLE</summary>

外部キーに`NULL`があることを許可します。これがデフォルトです。

外部キーに`NULL`があるとき、その行は被参照テーブルを参照できません。

```sql
SIMPLE
```

</details>

<details><summary>PARTIAL</summary>

まだ実装されていません。

</details>

</details>

<details><summary>ON DELETE</summary>

被参照行が削除された場合の動作を指定する。

```sql
ON DELETE {NO ACTION | RESTRICT | CASCADE | SET NULL | SET DEFAULT}
```

### 句

<details><summary>NO ACTION</summary>

エラーを発生させる。デフォルトの動作。制約の検査と同時に行われる。

```sql
NO ACTION
```

</details>

<details><summary>RESTRICT</summary>

エラーを発生させる。制約の検査を同時に行われるが、検査を遅延することはできない。

```sql
RESTRICT
```

</details>

<details><summary>CASCADE</summary>

被参照行が削除されたとき、参照している行すべてを削除する。

```sql
CASCADE
```

</details>

<details><summary>SET NULL</summary>

外部キー列を`NULL`にします。

```sql
SET NULL
```

</details>

<details><summary>SET DEFAULT</summary>

外部キー列をデフォルト値にします。設定されたデフォルトの値が

被参照テーブルに存在しない場合は、操作が失敗します。

```sql
SET DEFAULT
```

</details>

</details>

<details><summary>ON UPDATE</summary>

被参照列が更新された場合の動作を指定する。

```sql
ON DELETE {NO ACTION | RESTRICT | CASCADE | SET NULL | SET DEFAULT}
```

#### 句

<details><summary>RESTRICT</summary>

エラーを発生させる。制約の検査を同時に行われるが、検査を遅延することはできない。

```sql
RESTRICT
```

</details>

<details><summary>CASCADE</summary>

値を更新します。

```sql
CASCADE
```

</details>

<details><summary>SET NULL</summary>

外部キー列を`NULL`にします。

```sql
SET NULL
```

</details>

<details><summary>SET DEFAULT</summary>

外部キー列をデフォルト値にします。設定されたデフォルトの値が

被参照テーブルに存在しない場合は、操作が失敗します。

```sql
SET DEFAULT
```

</details>

</details>

</details>

<details><summary>DEFERRABLE</summary>

制約を遅延させることが可能になる。

遅延は`SET CONSTRAINTS`コマンドでトランザクション終了まで

遅延させることができます。検査制約と非ナル値制約は遅延させることができません。

また、`INSERT`の`ON CONFLICT DO UPDATE`の競合解決に使用することはできません。

```sql
[NOT] DEFERRABLE
```

### 句

<details><summary>NOT</summary>

制約を遅延させることができなくなる。これがデフォルトです。

```sql
NOT
```

</details>

</details>

<details><summary>INITIALLY</summary>

制約が遅延可能なとき、制約検査を行うデフォルトのタイミングを指定します。

```sql
INITIALLY {IMMEDIATE | DEFERRED}
```

### 句

<details><summary>IMMEDIATE</summary>

各文の実行後すぐに検査します。これがデフォルトです。

```sql
IMMEDIATE
```

</details>

<details><summary>DEFERRED</summary>

トランザクションの終了時に検査されます。

```sql
DEFERRED
```

</details>

</details>

<details><summary>EXCLUDE</summary>

吐いた制約を設けます。

任意の2行について指定した列、または指定した式を使用して比較した時、

比較の結果がすべて`FALSE`を返すことを保証します。一意性制約や検査制約で

制御できないものを制御します。

```sql
EXCLUDE [USING] ({<exclude_element> WITH}[, ...]) <index_parameters> [WHERE]
```

### 句

<details><summary>USING</summary>

```sql
USING <index_method>
```

</details>

<details><summary>WITH</summary>

```sql
WITH <operator>[, ...]
```

</details>

<details><summary>WHERE</summary>

```sql
WHERE (<predicate>)
```

</details>

</details>

<details><summary>FOREIGN KEY</summary>

外部キーを複数の列をセットで指定するとき、テーブル制約の

この句を使用する。

```sql
FOREIGN KEY (<column_name>[, ...])
    REFERENCES <ref_table> [(<ref_column>[, ...])]
```

### パラメータ

<details><summary>ref_column</summary>

非参照列キー、指定しなかった場合は、主キーが自動的に

割り当てられる。

</details>

</details>

<details><summary>INHERITS</summary>

テーブルの全ての列を継承する。通常のテーブルと外部テーブルを指定できます。

親のスキーマ変更は子にも伝播します。デフォルトでは親の操作結果には

子テーブルのデータも含まれます。複数の親テーブルに同名の列が存在する場合、

同じデータ型である必要があります。`IDENTITY`列だけは継承されないので、

子テーブルにも宣言が必要です。

```sql
INHERITS (<parent_table>[, ...])
```

</details>

<details><summary>PARTITION BY</summary>

パーティションキーを作成します。

別に`CREATE TABLE PARTITION OF`コマンドで

パーティションキーで副テーブルを作成します。

```sql
PARTITION BY {RANGE | LIST | HASH}
    ({{<column_name> | (<expression>)} [<op_class>]}[, ...])
```

### パラメータ

<details><summary>column_name</summary>

パーティションキーに含める列

</details>

<details><summary>expression</summary>

パーティションキーに含める式

</details>

<details><summary>op_class</summary>

インデックスメソッド。省略した場合、`btree`インデックスになる。

</details>

### 句

<details><summary>RANGE</summary>

範囲パーティション。異なるパーティションの範囲が被らないようにある。

インデックスには少なくともひとつ`btree`インデックスを必要とします。

```sql
RANGE
```

</details>

<details><summary>LIST</summary>

リストパーティション。指定した列だけでパーティションを作成する。

インデックスには少なくともひとつ`btree`インデックスを必要とします。

```sql
LIST
```

</details>

<details><summary>HASH</summary>

ハッシュパーティション。ハッシュインデックスを使用します。

```sql
HASH
```

</details>

</details>

<details><summary>AS</summary>

問い合わせ文の結果からテーブルを作成します。

テーブルの構造とともに、データもコピーされます。

```sql
AS <query> [WITH DATA]
```

### 句

<details><summary>WITH DATA</summary>

データも一緒に新しいテーブルにコピーします。

デフォルトはコピーします。

```sql
WITH [NO] DATA
```

#### 句

<details><summary>NO</summary>

データはコピーせず、構造だけコピーします。

```sql
NO
```

</details>

</details>

</details>

<details><summary>PARTITION OF</summary>

指定した親テーブルのパーティションテーブルを作成する。

```sql
PARTITION OF <parent_table>
    [(
        {
            <column_name> WITH OPTIONS [COLLATE]
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
    )]
    {FOR VALUES}
```

### パラメータ

<details><summary>parent_table</summary>

パーティションキーが作成されているテーブル

</details>

### 句

<details><summary>FOR VALUES</summary>

```sql
{FOR VALUES {IN | FROM | TO | WITH} | DEFAULT}
```

#### 句

<details><summary>IN</summary>

```sql
IN (<partition_bound_expr>[, ...])
```

</details>

<details><summary>FROM</summary>

```sql
FROM ({<partition_bound_expr> | MINVALUE | MAXVALUE}[, ...])
```

</details>

<details><summary>TO</summary>

```sql
TO ({<partition_bound_expr> | MINVALUE | MAXVALUE}[, ...])
```

</details>

<details><summary>WITH</summary>

```sql
WITH (MODULUS <numeric_literal>, REMAINDER <numeric_literal>)
```

</details>

</details>

</details>

<details><summary>OF</summary>

型付きテーブルを作成する。

```sql
OF <type_name>
    [(
        {
            <column_name> WITH OPTIONS [COLLATE]
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
    )]
    {FOR VALUES | DEFAULT}
```
</details>

<details><summary>LIKE</summary>

指定したテーブルの列名、データ型、制約を新しいテーブルに

コピーします。`INHERITS`とは違い、新しいと元のテーブルは完全に

分離されます。

```sql
LIKE <source_table> [EXCLUDING | INCLUDING]
```

### パラメータ

<details><summary>source_table</summary>

コピーするテーブル。

</details>

### 句

<details><summary>EXCLUDING</summary>

追加属性をコピーしない。これはデフォルトです。

```sql
EXCLUDING
```

</details>

<details><summary>INCLUDING</summary>

```sql
INCLUDING {
    COMMENTS
    | CONSTRAINTS
    | DEFAULTS
    | GENERATED
    | IDENTITY
    | INDEXES
    | STATISTICS
    | STORAGE
    | ALL
}
```

</details>

</details>

<details><summary>USING</summary>

テーブルアクセスメソッドを指定します。

```sql
USING <method>
```

</details>

<details><summary>WITH</summary>

この句はテーブルまたはインデックスに対するオプションの

格納パラメータを指定します。

```sql
WITH ({<storage_parameter[= <value>]>}[, ...])
```

</details>

<details><summary>ON COMMIT</summary>

トランザクション終了時のテーブルの動作を指定する。

```sql
ON COMMIT {PRESERVE ROWS | DELETE ROWS | DROP}
```

### 句

<details><summary>PRESERVE ROWS</summary>

特別な動作は実行しません。これがデフォルトです。

</details>

<details><summary>DELETE ROWS</summary>

すべての行が削除される。

```sql
DELETE ROWS
```

</details>

<details><summary>DROP</summary>

テーブルが削除される。

```sql
DROP
```

</details>

</details>

<details><summary>TABLESPACE</summary>

インデックスを作成するテーブル空間を作成します。

省略された場合、デフォルトのテーブル空間が自動的に作成されます。

```sql
TABLESPACE <tablespace_name>
```

</details>
