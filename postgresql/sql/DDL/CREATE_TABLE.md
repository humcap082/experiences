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

<details><summary>table_name</summary><section>

作成するテーブル名

</section></details>

<details><summary>column_name</summary><section>

テーブルに作成する列名

</section></details>

<details><summary>data_type</summary><section>

列のデータ型

</section></details>

## 句

<details><summary>TEMP</summary><section>

一時テーブルとする。`TEMPORARY`でもよい。

一時テーブルは現在のセッションやトランザクションの終わりに自動的に削除される。

一時テーブルのインデックスも一時的なものになります。

既に存在するテーブル名と被った場合は、一時テーブルが優先して参照されます。

```TEMP
TEMP
```

</section></details>

<details><summary>UNLOGGED</summary><section>

ログをとらないテーブルとする。

ログをとらないため、相当高速になるが、クラッシュ時に安全ではなくなる。

```sql
UNLOGGED
```

</section></details>

<details><summary>IF NOT EXISTS</summary><section>

同じ名前のテーブルが存在していてもエラーになりません。

かわりに注意が発せられます。

```sql
IF NOT EXISTS
```

</section></details>

<details><summary>COLLATE</summary><section>

文字列の比較やソートの照合順を指定します。`text, varchar, char`などの文字列の列に定義できます。

デフォルトは`"default`でデータベースの`lc_collate`に依存します。

```sql
COLLATE "<collation>"
```

<details><summary>collation</summary><section>

照合順序

|照合順序|説明|
|:---|:---|
|default|ローカルの言語に依存|
|C|ASCIIに準拠|
|POSIX|ASCIIに準拠|
|ucs_basic|Unicodeに準拠|

</section></details>

</section></details>

<details><summary>CONSTRAINT</summary><section>

列制約、テーブル制約の名前。列や、テーブルにかけられた制約に名前を指定できる。

列名の直後に記述すると、その列の制約名になり、列のリストの一つとして記述した場合は

そのテーブルの制約名になる。

```sql
CONSTRAINT <constraint_name>
```

</section></details>

<details><summary>NULL</summary><section>

その列が`NULL`をもてることを指定する。これがデフォルト。


```sql
[NOT] NULL
```

### 句

<details><summary>NOT</summary><section>

その列が`NULL`をもてないことを指定する。

</section></details>

</section></details>

<details><summary>CHECK</summary><section>

検査制約を指定する。

新しい行、または行が更新された時に満たす必要がある条件を記述します。

`TRUE`と`UNKNOWN`と評価される式は成功します。列制約として指定された

検査制約はその列のみを参照できます。テーブル制約として指定された検査制約は

複数の列を参照できます。現在、他の列、変数は検査制約では使用できません。

```sql
CHECK (<expression>) [NO INHERIT]
```

### パラメータ

<details><summary>expression</summary><section>

真偽値を返す条件を記述します。列制約の場合は、その列のみを参照でき、

テーブル制約として指定された場合は、そのテーブルの列を参照できる。

</section></details>

### 句

<details><summary>NO INHERIT</summary><section>

この句を含む場合、子テーブルには制約が伝搬しない。

```sql
NO INHERIT
```

</section></details>

</section></details>

<details><summary>DEFAULT</summary><section>

その列にデフォルトの値が割り当てられる。値が設定されなかった場合に

指定された値がデフォルトではいる。この句を指定しなかった場合、

デフォルトは`NULL`。

```sql
DEFAULT <default_expr>
```

### パラメータ

<details><summary>default_expr</summary><section>

デフォルトになる値。変数は含められず、サブクエリも、他の列の値も

含めることもできない。

</section></details>

</section></details>

<details><summary>GENERATED</summary><section>

ユーザーは列の値を指定できず、自動的に値を生成する列になる。

```sql
GENERATED {
    ALWAYS AS (<generation_expr>) STORED 
    | {ALWAYS | BY DEFAULT} AS IDENTITY
}
```

### パラメータ

<details><summary>generation_expr</summary><section>

自動的に生成する値の式。そのテーブルの他の列を参照することができます。

使用される演算子や関数はイミュータブルでなければなりません。

</section></details>

### 句

<details><summary>ALWAYS</summary><section>

行を挿入時に`INSERT`に`OVERRIDING SYSTEM VALUE`を指定しないと、

上書きすることができない。

```sql
ALWAYS
```

</section></details>

<details><summary>BY DEFAULT</summary><section>

行を挿入時に`INSERT`に`OVERRIDING USER VALUE`を指定しないと

上書きをすることができない。

```sql
BY DEFAULT
```

</section></details>

<details><summary>AS IDENTITY</summary><section>

シーケンスと暗示的に紐づけられ、シーケンスからとられた値が自動的にはいる。

```sql
AS IDENTITY [(<sequence_options>)]
```

#### パラメータ

<details><summary>sequence_options</summary><section>

`CREATE SEQUENCE`に使用されるオプション句を指定できる。

</section></details>

</section></details>

</section></details>

<details><summary>UNIQUE</summary><section>

一意性制約を設ける。一意性制約では`NULL`値は等しいとみなされません。

一意性制約を設けると`btree`インデックスが自動的に作成されます。

複数の列をセットで一意とみなす場合はテーブル制約を使用します。

```sql
UNIQUE -- 列制約
UNIQUE (<column_name>[, ...]) [INCLUDE] -- テーブル制約
```

### 句

<details><summary>INCLUDE</summary><section>

一意でない列を明示的に指定することができる。

```sql
INCLUDE (<column_name>[, ...])
```

</section></details>

</section></details>

<details><summary>PRIMARY KEY</summary><section>

主キー制約を設ける。主キー制約は一意であり、非`NULL`である必要があり、

1つのテーブルに1つだけ指定できます。

主キーには`bree`インデックスが自動的に作成されます。

```sql
PRIMARY KEY  -- 列制約
PRIMARY KEY (<column_name>[, ...]) [INCLUDE] -- 表制約
```

### 句

<details><summary>INCLUDE</summary><section>

一意でない列を明示的に指定することができる。

```sql
INCLUDE (<column_name>[, ...])
```

</section></details>

</section></details>

<details><summary>REFERENCES</summary><section>

外部キー制約を設ける。一時テーブルとの間に外部キー制約を設けることはできない。

```sql
REFERENCES <ref_table> [(<ref_column>)] [MATCH] [ON DELETE] [ON UPDATE]
```

### パラメータ

<details><summary>ref_table</summary><section>

被参照テーブル。

</section></details>

<details><summary>ref_column</summary><section>

被参照列。省略した場合は、被参照テーブルの主キーになる。

被参照列は主キー制約もしくは一意性制約が設けられてる必要があります。

</section></details>

### 句

<details><summary>MATCH</summary><section>

照合型を指定する。

```MATCH
MATCH {FULL | PARTIAL | SIMPLE}
```

#### 句

<details><summary>FULL</summary><section>

複数、外部キーがあるとき、一部が`NULL`であることを許可しない。

全ての外部キーが`NULL`であるときは、被参照テーブルを参照できないものとして

許可される。

```sql
FULL
```

</section></details>

<details><summary>SIMPLE</summary><section>

外部キーに`NULL`があることを許可します。これがデフォルトです。

外部キーに`NULL`があるとき、その行は被参照テーブルを参照できません。

```sql
SIMPLE
```

</section></details>

<details><summary>PARTIAL</summary><section>

まだ実装されていません。

</section></details>

</section></details>

<details><summary>ON DELETE</summary><section>

被参照行が削除された場合の動作を指定する。

```sql
ON DELETE {NO ACTION | RESTRICT | CASCADE | SET NULL | SET DEFAULT}
```

### 句

<details><summary>NO ACTION</summary><section>

エラーを発生させる。デフォルトの動作。制約の検査と同時に行われる。

```sql
NO ACTION
```

</section></details>

<details><summary>RESTRICT</summary><section>

エラーを発生させる。制約の検査を同時に行われるが、検査を遅延することはできない。

```sql
RESTRICT
```

</section></details>

<details><summary>CASCADE</summary><section>

被参照行が削除されたとき、参照している行すべてを削除する。

```sql
CASCADE
```

</section></details>

<details><summary>SET NULL</summary><section>

外部キー列を`NULL`にします。

```sql
SET NULL
```

</section></details>

<details><summary>SET DEFAULT</summary><section>

外部キー列をデフォルト値にします。設定されたデフォルトの値が

被参照テーブルに存在しない場合は、操作が失敗します。

```sql
SET DEFAULT
```

</section></details>

</section></details>

<details><summary>ON UPDATE</summary><section>

被参照列が更新された場合の動作を指定する。

```sql
ON DELETE {NO ACTION | RESTRICT | CASCADE | SET NULL | SET DEFAULT}
```

#### 句

<details><summary>RESTRICT</summary><section>

エラーを発生させる。制約の検査を同時に行われるが、検査を遅延することはできない。

```sql
RESTRICT
```

</section></details>

<details><summary>CASCADE</summary><section>

値を更新します。

```sql
CASCADE
```

</section></details>

<details><summary>SET NULL</summary><section>

外部キー列を`NULL`にします。

```sql
SET NULL
```

</section></details>

<details><summary>SET DEFAULT</summary><section>

外部キー列をデフォルト値にします。設定されたデフォルトの値が

被参照テーブルに存在しない場合は、操作が失敗します。

```sql
SET DEFAULT
```

</section></details>

</section></details>

</section></details>

<details><summary>DEFERRABLE</summary><section>

制約を遅延させることが可能になる。

遅延は`SET CONSTRAINTS`コマンドでトランザクション終了まで

遅延させることができます。検査制約と非ナル値制約は遅延させることができません。

また、`INSERT`の`ON CONFLICT DO UPDATE`の競合解決に使用することはできません。

```sql
[NOT] DEFERRABLE
```

### 句

<details><summary>NOT</summary><section>

制約を遅延させることができなくなる。これがデフォルトです。

```sql
NOT
```

</section></details>

</section></details>

<details><summary>INITIALLY</summary><section>

制約が遅延可能なとき、制約検査を行うデフォルトのタイミングを指定します。

```sql
INITIALLY {IMMEDIATE | DEFERRED}
```

### 句

<details><summary>IMMEDIATE</summary><section>

各文の実行後すぐに検査します。これがデフォルトです。

```sql
IMMEDIATE
```

</section></details>

<details><summary>DEFERRED</summary><section>

トランザクションの終了時に検査されます。

```sql
DEFERRED
```

</section></details>

</section></details>

<details><summary>EXCLUDE</summary><section>

吐いた制約を設けます。

任意の2行について指定した列、または指定した式を使用して比較した時、

比較の結果がすべて`FALSE`を返すことを保証します。一意性制約や検査制約で

制御できないものを制御します。

```sql
EXCLUDE [USING] ({<exclude_element> WITH}[, ...]) <index_parameters> [WHERE]
```

### 句

<details><summary>USING</summary><section>

```sql
USING <index_method>
```

</section></details>

<details><summary>WITH</summary><section>

```sql
WITH <operator>[, ...]
```

</section></details>

<details><summary>WHERE</summary><section>

```sql
WHERE (<predicate>)
```

</section></details>

</section></details>

<details><summary>FOREIGN KEY</summary><section>

外部キーを複数の列をセットで指定するとき、テーブル制約の

この句を使用する。

```sql
FOREIGN KEY (<column_name>[, ...])
    REFERENCES <ref_table> [(<ref_column>[, ...])]
```

### パラメータ

<details><summary>ref_column</summary><section>

非参照列キー、指定しなかった場合は、主キーが自動的に

割り当てられる。

</section></details>

</section></details>

<details><summary>INHERITS</summary><section>

テーブルの全ての列を継承する。通常のテーブルと外部テーブルを指定できます。

親のスキーマ変更は子にも伝播します。デフォルトでは親の操作結果には

子テーブルのデータも含まれます。複数の親テーブルに同名の列が存在する場合、

同じデータ型である必要があります。`IDENTITY`列だけは継承されないので、

子テーブルにも宣言が必要です。

```sql
INHERITS (<parent_table>[, ...])
```

</section></details>

<details><summary>PARTITION BY</summary><section>

パーティションキーを作成します。

別に`CREATE TABLE PARTITION OF`コマンドで

パーティションキーで副テーブルを作成します。

```sql
PARTITION BY {RANGE | LIST | HASH}
    ({{<column_name> | (<expression>)} [<op_class>]}[, ...])
```

### パラメータ

<details><summary>column_name</summary><section>

パーティションキーに含める列

</section></details>

<details><summary>expression</summary><section>

パーティションキーに含める式

</section></details>

<details><summary>op_class</summary><section>

インデックスメソッド。省略した場合、`btree`インデックスになる。

</section></details>

### 句

<details><summary>RANGE</summary><section>

範囲パーティション。異なるパーティションの範囲が被らないようにある。

インデックスには少なくともひとつ`btree`インデックスを必要とします。

```sql
RANGE
```

</section></details>

<details><summary>LIST</summary><section>

リストパーティション。指定した列だけでパーティションを作成する。

インデックスには少なくともひとつ`btree`インデックスを必要とします。

```sql
LIST
```

</section></details>

<details><summary>HASH</summary><section>

ハッシュパーティション。ハッシュインデックスを使用します。

```sql
HASH
```

</section></details>

</section></details>

<details><summary>AS</summary><section>

問い合わせ文の結果からテーブルを作成します。

テーブルの構造とともに、データもコピーされます。

```sql
AS <query> [WITH DATA]
```

### 句

<details><summary>WITH DATA</summary><section>

データも一緒に新しいテーブルにコピーします。

デフォルトはコピーします。

```sql
WITH [NO] DATA
```

#### 句

<details><summary>NO</summary><section>

データはコピーせず、構造だけコピーします。

```sql
NO
```

</section></details>

</section></details>

</section></details>

<details><summary>PARTITION OF</summary><section>

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

<details><summary>parent_table</summary><section>

パーティションキーが作成されているテーブル

</section></details>

### 句

<details><summary>FOR VALUES</summary><section>

```sql
{FOR VALUES {IN | FROM | TO | WITH} | DEFAULT}
```

#### 句

<details><summary>IN</summary><section>

```sql
IN (<partition_bound_expr>[, ...])
```

</section></details>

<details><summary>FROM</summary><section>

```sql
FROM ({<partition_bound_expr> | MINVALUE | MAXVALUE}[, ...])
```

</section></details>

<details><summary>TO</summary><section>

```sql
TO ({<partition_bound_expr> | MINVALUE | MAXVALUE}[, ...])
```

</section></details>

<details><summary>WITH</summary><section>

```sql
WITH (MODULUS <numeric_literal>, REMAINDER <numeric_literal>)
```

</section></details>

</section></details>

</section></details>

<details><summary>OF</summary><section>

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
</section></details>

<details><summary>LIKE</summary><section>

指定したテーブルの列名、データ型、制約を新しいテーブルに

コピーします。`INHERITS`とは違い、新しいと元のテーブルは完全に

分離されます。

```sql
LIKE <source_table> [EXCLUDING | INCLUDING]
```

### パラメータ

<details><summary>source_table</summary><section>

コピーするテーブル。

</section></details>

### 句

<details><summary>EXCLUDING</summary><section>

追加属性をコピーしない。これはデフォルトです。

```sql
EXCLUDING
```

</section></details>

<details><summary>INCLUDING</summary><section>

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

</section></details>

</section></details>

<details><summary>USING</summary><section>

テーブルアクセスメソッドを指定します。

```sql
USING <method>
```

</section></details>

<details><summary>WITH</summary><section>

この句はテーブルまたはインデックスに対するオプションの

格納パラメータを指定します。

```sql
WITH ({<storage_parameter[= <value>]>}[, ...])
```

</section></details>

<details><summary>ON COMMIT</summary><section>

トランザクション終了時のテーブルの動作を指定する。

```sql
ON COMMIT {PRESERVE ROWS | DELETE ROWS | DROP}
```

### 句

<details><summary>PRESERVE ROWS</summary><section>

特別な動作は実行しません。これがデフォルトです。

</section></details>

<details><summary>DELETE ROWS</summary><section>

すべての行が削除される。

```sql
DELETE ROWS
```

</section></details>

<details><summary>DROP</summary><section>

テーブルが削除される。

```sql
DROP
```

</section></details>

</section></details>

<details><summary>TABLESPACE</summary><section>

インデックスを作成するテーブル空間を作成します。

省略された場合、デフォルトのテーブル空間が自動的に作成されます。

```sql
TABLESPACE <tablespace_name>
```

</section></details>
