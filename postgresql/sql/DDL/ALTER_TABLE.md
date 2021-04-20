# ALTER TABLE

テーブルの定義を変更する。

```sql
ALTER TABLE [IF EXISTS] [ONLY] {
    <name> {
        RENAME
        | SET
        | ATTACH PARTITION
        | DETACH PARTITION
        | ADD
        | DROP
        | ALTER
        | VALIDATE CONSTRAINT
        | DISABLE
        | ENABLE
        | FORCE ROW LEVEL SECURITY
        | CLUSTER ON
        | RESET
        | INHERIT
        | OF
        | NOT OF
        | OWNER TO
        | REPLICA IDENTITY
    }[, ...]
    | ALL IN TABLESPACE
}
```

## パラメータ

<details><summary>name</summary>

変更対象となる既存のテーブル名

</details>

## 句

<details><summary>IF EXISTS</summary>

```sql
IF EXISTS
```

</details>

<details><summary>ONLY</summary>

```sql
ONLY
```

</details>

<details><summary>RENAME</summary>

```sql
RENAME [[COLUMN] <column_name>| CONSTRAINT] TO
```

### パラメータ

<details><summary>column_name</summary>
</details>

### 句

<details><summary>COLUMN</summary>

```sql
COLUMN
```

</details>

<details><summary>CONSTRAINT</summary>

```sql
CONSTRAINT <constraint_name>
```

</details>

<details><summary>TO</summary>

```sql
TO <new_name>
```

### パラメータ

<details><summary>new_name</summary>
</details>

</details>

</details>

<details><summary>SET</summary>

```sql
SET {
    SCHEMA
    | WITHOUT CLUSTER
    | WITHOUT OIDS
    | TABLESPACE
    | {LOGGED | UNLOGGED}
    | (<storage_parameter>[= <value>][, ...])
}
```

### パラメータ

<details><summary>storage_parameter</summary>
</details>

<details><summary>value</summary>
</details>

### 句

<details><summary>SCHEMA</summary>

```sql
SCHEMA <new_schema>
```

#### パラメータ

<details><summary>new_schema</summary>
</details>

</details>

<details><summary>WITHOUT CLUSTER</summary>

```sql
WITHOUT CLUSTER
```

</details>

<details><summary>WITHOUT OIDS</summary>

```sql
WITHOUT OIDS
```

</details>

<details><summary>TABLESPACE</summary>

```sql
TABLESPACE <new_tablespace>
```

#### パラメータ

<details><summary>new_tablespace</summary>
</details>

</details>

<details><summary>LOGGED</summary>

```sql
LOGGED
```

</details>

<details><summary>UNLOGGED</summary>

```sql
UNLOGGED
```

</details>

</details>

<details><summary>ATTACH PARTITION</summary>

```sql
ATTACH PARTITION <partition_name> {FOR VALUES | DEFAULT}
```

### パラメータ

<details><summary>partition_name</summary>
</details>

### 句

<details><summary>FOR VALUES</summary>

```sql
FOR VALUES {IN | FROM | TO | WITH}
```

#### 句

<details><summary>IN</summary>

```sql
IN (<partition_bound_expr>[, ...])
```

##### パラメータ

<details><summary>partition_bound_expr</summary>
</details>

</details>

<details><summary>FROM</summary>

```sql
FROM ({<partition_bound_expr> | MINVALUE | MAXVALUE}[, ...])
```

##### パラメータ

<details><summary>partition_bound_expr</summary>
</details>

</details>

<details><summary>TO</summary>

```sql
TO ({<partition_bound_expr> | MINVALUE | MAXVALUE}[, ...])
```

##### パラメータ

<details><summary>partition_bound_expr</summary>
</details>

</details>

<details><summary>WITH</summary>

```sql
WITH (MODULUS <numeric_literal>, REMAINDER <numeric_literal>)
```

</details>

</details>

<details><summary>DEFAULT</summary>

```sql
DEFAULT
```

</details>

</details>

<details><summary>DETACH PARTITION</summary>

```sql
DETACH PARTITION <partition_name>
```

### パラメータ

<details><summary>partition_name</summary>
</details>

</details>

<details><summary>ADD</summary>

```sql
ADD {
    [COLUMN] [IF NOT EXISTS] <column_name> <data_type>
        [COLLATE] [<column_constraint>]
    | <table_constraint> [NOT VALID]
}
```

### パラメータ

<details><summary>column_name</summary>
</details>

<details><summary>data_type</summary>
</details>

<details><summary>column_constraint</summary>
</details>

<details><summary>table_constraint</summary>
</details>

### 句

<details><summary>COLUMN</summary>

```sql
COLUMN
```

</details>

<details><summary>IF NOT EXISTS</summary>

```sql
IF NOT EXISTS
```

</details>

<details><summary>COLLATE</summary>

```sql
COLLATE <collation>
```

#### パラメータ

<details><summary>collation</summary>
</details>

</details>

<details><summary>NOT VALID</summary>

```sql
NOT VALID
```

</details>

</details>

<details><summary>DROP</summary>

```sql
DROP {
    [COLUMN] [IF EXISTS] <column_name>
    | CONSTRAINT
} [RESTRICT | CASCADE]
```

### パラメータ

<details><summary>column_name</summary>
</details>

### 句

<details><summary>IF EXISTS</summary>

```sql
IF EXISTS
```

</details>

<details><summary>CONSTRAINT</summary>

```sql
CONSTRAINT [IF EXISTS] <constraint_name>
```

### パラメータ

<details><summary>constraint_name</summary>
</details>

### 句

<details><summary>IF EXISTS</summary>

```sql
IF EXISTS
```

</details>

</details>

<details><summary>RESTRICT</summary>

```sql
RESTRICT
```

</details>

<details><summary>CASCADE</summary>

```sql
CASCADE
```

</details>

</details>

<details><summary>ALTER</summary>

```sql
ALTER {
    [COLUMN] <column_name> {
        TYPE
        | SET
        | ADD GENERATED
        | DROP
        | RESET
    }
}
```

### パラメータ

<details><summary>column_name</summary>
</details>

### 句

<details><summary>TYPE</summary>

```sql
[SET DATA] TYPE <data_type> [COLLATE] [USING]
```

#### パラメータ

<details><summary>data_type</summary>
</details>

#### 句

<details><summary>SET DATA</summary>

```sql
SET DATA
```

</details>

<details><summary>COLLATE</summary>

```sql
COLLATE <collation>
```

##### パラメータ

<details><summary>collation</summary>
</details>

</details>

<details><summary>USING</summary>

```sql
USING <expression>
```

## パラメータ

<details><summary>expression</summary>
</details>

</details>

</details>

<details><summary>SET</summary>

```sql
SET {
    DEFAULT
    | STATISTICS
    | STORAGE
    | ({<attribute_option> = <value>}[, ...])
}
```

#### 句

<details><summary>DEFAULT</summary>

```sql
DEFAULT <expression>
```

##### パラメータ

<details><summary>expression</summary>
</details>

</details>

<details><summary>STATISTICS</summary>

```sql
STATISTICS <integer>
```

##### パラメータ

<details><summary>integer</summary>
</details>

</details>

<details><summary>STORAGE</summary>

```sql
STORAGE {PLAIN | EXTERNAL | EXTENDED | MAIN}
```

##### 句

<details><summary>PLAIN</summary>

```sql
PLAIN
```

</details>

<details><summary>EXTENDED</summary>

```sql
EXTENDED
```

</details>

<details><summary>MAIN</summary>

```sql
MAIN
```

</details>

</details>

</details>

<details><summary>ADD GENERATED</summary>

```sql
ADD GENERATED {ALWAYS | BY DEFUALT} AS IDENTITY
```

### パラメータ

<details><summary>ALWAYS</summary>

```sql
ALWAYS
```

</details>

<details><summary>BY DEFAULT</summary>

```sql
BY DEFAULT
```

</details>

<details><summary>AS IDENTITY</summary>

```sql
AS IDENTITY [(<sequence_options>)]
```

##### パラメータ

<details><summary>sequence_options</summary>
</details>

</details>

</details>

<details><summary>DROP</summary>

```sql
DROP {DEFAULT | IDENTITY}
```

#### 句

<details><summary>DEFAULT</summary>

```sql
DEFAULT
```

</details>

<details><summary>IDENTITY</summary>

```sql
IDENTITY [IF EXISTS]
```

##### 句

<details><summary>IF EXISTS</summary>

```sql
IF EXISTS
```

</details>

</details>

</details>

<details><summary>RESET</summary>

```sql
RESET (<attribute_option>[, ...])
```

#### パラメータ

<details><summary>attribute_option</summary>
</details>

</details>

</details>

<details><summary>VALIDATE CONSTRAINT</summary>

```sql
VALIDATE CONSTRAINT <constraint_name>
```

### パラメータ

<details><summary>constraint_name</summary>
</details>

</details>

<details><summary>DISABLE</summary>

```sql
DISABLE {TRIGGER | RULE | ROW LEVEL SECURITY}
```

### 句

<details><summary>TRIGGER</summary>

```sql
TRIGGER [<trigger_name> | ALL | USER]
```

#### パラメータ

<details><summary>trigger_name</summary>
</details>

#### 句

<details><summary>ALL</summary>

```sql
ALL
```

</details>

<details><summary>USER</summary>

```sql
USER
```

</details>

</details>

<details><summary>RULE</summary>

```sql
RULE <rewrite_rule_name>
```

#### パラメータ

<details><summary>rewrite_rule_name</summary>
</details>

</details>

<details><summary>ROW LEVEL SECURITY</summary>

```sql
ROW LEVEL SECURITY
```

</details>

</details>

<details><summary>ENABLE</summary>

```sql
ENABLE {
    [REPLICA | ALWAYS] {TRIGGER | RULE}
    | ROW LEVEL SECURITY
}
```

### 句

<details><summary>REPLICA</summary>

```sql
REPLICA
```

</details>

<details><summary>ALWAYS</summary>

```sql
ALWAYS
```

</details>

<details><summary>TRIGGER</summary>

```sql
TRIGGER {<trigger_name> | ALL | USER}
```

</details>

<details><summary>RULE</summary>

```sql
RULE <rewrite_rule_name>
```

</details>

<details><summary>ROW LEVEL SECURITY</summary>

```sql
ROW LEVEL SECURITY
```

</details>

</details>

<details><summary>FORCE ROW LEVEL SECURITY</summary>

```sql
[NO] FORCE ROW LEVEL SECURITY
```

</details>

<details><summary>CLUSTER ON</summary>

```sql
CLUSTER ON <index_name>
```

### パラメータ

<details><summary>index_name</summary>
</details>

</details>

<details><summary>RESET</summary>

```sql
RESET (<storage_parameter>, ...)
```

### パラメータ

<details><summary>storage_parameter</summary>
</details>

</details>

<details><summary>INHERIT</summary>

```sql
INHERIT <parent_table>
```

### パラメータ

<details><summary>parent_table</summary>
</details>

</details>

<details><summary>OF</summary>

```sql
OF <type_name>
```

### パラメータ　

<details><summary>type_name</summary>
</details>

</details>

<details><summary>NOT OF</summary>

```sql
NOT OF
```

</details>

<details><summary>OWNER TO</summary>

```sql
OWNER TO {<new_owner> | CURRENT_USER | SESSION_USER}
```

### パラメータ

<details><summary>new_owner</summary>
</details>

### 句

<details><summary>CURRENT_USER</summary>
</details>

<details><summary>SESSION_USER</summary>
</details>

</details>

<details><summary>REPLICA IDENTITY</summary>

```sql
REPLICA IDENTITY {DEFAULT | USING INDEX | FULL | NOTHING}
```

### 句

<details><summary>DEFAULT</summary>

```sql
DEFAULT
```

</details>

<details><summary>USING INDEX</summary>

```sql
USING INDEX <index_name>
```

</details>

<details><summary>FULL</summary>

```sql
FULL
```

</details>

<details><summary>NOTHING</summary>

```sql
NOTHING
```

</details>

</details>

<details><summary>ALL IN TABLESPACE</summary>

```sql
ALL IN TABLE SPACE <name> [OWNED BY]
```

### パラメータ

<details><summary>name</summary>
</details>

### 句

<details><summary>OWNED BY</summary>

```sql
OWNED BY <role_name>[, ...]
```

</details>

</details>
