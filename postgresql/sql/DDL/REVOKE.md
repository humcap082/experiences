# REVOKE

アクセス権限を取り消す。

```sql
REVOKE [ADMIN OPTION FOR | GRANT OPTION FOR] {
    {
        [SELECT] [, INSERT] [, UPDATE] [, DELETE]
            [, TRUNCATE] [, REFERENCES] [, TRIGGER]
            [, USAGE] [, CREATE] [, CONNECT] [, TEMP]
            [, EXECUTE]
        | ALL
    } ON
    | <role_name>[, ...]
} FROM [CASCADE | RESTRICT] [GRANTED BY]
```

## 句

<details><summary>SELECT</summary>

`SELECT`権限

```sql
SELECT [(<column_name>[, ...])]
```

</details>

<details><summary>INSERT</summary>

`INSERT`権限

```sql
INSERT [(<column_name>[, ...])]
```

</details>

<details><summary>UPDATE</summary>

`UPDATE`権限

```sql
UPDATE [(<column_name>[, ...])]
```

</details>

<details><summary>DELETE</summary>

`DELETE`権限

```sql
DELETE
```

</details>

<details><summary>TRUNCATE</summary>

`TRUNCATE`権限

```sql
TRUNCATE
```

</details>

<details><summary>REFERENCES</summary>

外部キー制約を作成できる権限

```sql
REFERENCES [(<column_name>[, ...])]
```

</details>

<details><summary>TRIGGER</summary>

トリガを作成できる権限。

```sql
TRIGGER
```

</details>

<details><summary>USAGE</summary>

```sql
USAGE
```

</details>

<details><summary>CREATE</summary>

新しいスキーマやパブリケーションを作成できる権限

```sql
CREATE
```

</details>

<details><summary>CONNECT</summary>

データベースに接続する権限。

```sql
CONNECT
```

</details>

<details><summary>TEMP</summary>

一時テーブルを作成する権限。`TEMPORARY`と同等

```sql
TEMP
```

</details>

<details><summary>EXECUTE</summary>

関数の呼び出し権限。

```sql
EXECUTE
```

</details>

<details><summary>ALL</summary>

すべての権限。

```sql
ALL [PRIVILEGES] [(<column_name>[, ...])]
```

#### パラメータ

<details><summary>column_name</summary>

</details>

</details>

<details><summary>ON</summary>

```sql
ON {
    <table_name>[, ...]
    | ALL
    | SEQUENCE
    | DATABASE
    | DOMAIN
    | FOREIGN DATA WRAPPER
    | FOREIGN SERVER
    | FUNCTION
    | ROUTINE
    | LANGUAGE
    | LARGE OBJECT
    | TYPE
    | SCHEMA
    | TABLESPACE
}
```

### パラメータ

<details><summary>table_name</summary>

</details>

### 句

<details><summary>ALL</summary>

```sql
ALL {TABLES | SEQUENCES | FUNCTIONS | ROUTINES} IN SCHEMA <schema_name>[, ...]
```

#### パラメータ

<details><summary>schema_name</summary>

</details>

#### 句

<details><summary>TABLES</summary>

```sql
TABLES
```

</details>

<details><summary>SEQUENCES</summary>

```sql
SEQUENCES
```

</details>

<details><summary>FUNCTIONS</summary>

```sql
FUNCTIONS
```

</details>

<details><summary>ROUTINES</summary>

```sql
ROUTINES
```

</details>

</details>

<details><summary>SEQUENCE</summary>

```sql
SEQUENCE <sequence_name>[, ...]
```

#### パラメータ

<details><summary>sequence_name</summary>

</details>

</details>

<details><summary>DATABASE</summary>

```sql
DATABASE <database_name>[, ...]
```

#### パラメータ

<details><summary>database_name</summary>
</details>

</details>

<details><summary>DOMAIN</summary>

```sql
DOMAIN <domain_name>[, ...]
```

#### パラメータ

<details><summary>domain_name</summary>
</details>

</details>

<details><summary>FOREIGN DATA WRAPPER</summary>

```sql
FOREIGN DATA WRAPPER <fdw_name>[,...]
```

<details><summary>fdw_name</summary>
</details>

</details>

<details><summary>FOREIGN SERVER</summary>

```sql
FOREIGN SERVER <server_name>[, ...]
```

#### パラメータ

<details><summary>server_name</summary>
</details>

</details>

<details><summary>FUNCTION</summary>

```sql
FUNCTION {<function_name> [({[<arg_mode] [arg_name] arg_type}[, ...])]}[, ...]
```

### パラメータ

<details><summary>function_name</summary>
</details>

<details><summary>arg_mode</summary>
</details>

<details><summary>arg_name</summary>
</details>

<details><summary>arg_type</summary>
</details>

</details>

<details><summary>ROUTINE</summary>

```sql
ROUTINE {<function_name> [({[<arg_mode] [arg_name] arg_type}[, ...])]}[, ...]
```

### パラメータ

<details><summary>function_name</summary>
</details>

<details><summary>arg_mode</summary>
</details>

<details><summary>arg_name</summary>
</details>

<details><summary>arg_type</summary>
</details>

</details>

<details><summary>LANGUAGE</summary>

```sql
LANGUAGE <lang_name>[, ...]
```

#### パラメータ

<details><summary>lang_name</summary>
</details>

</details>

<details><summary>LARGE OBJECT</summary>

```sql
LARGE OBJECT <loid>[, ...]
```

### パラメータ

<details><summary>loid</summary>
</details>

</details>

<details><summary>TYPE</summary>

```sql
TYPE <type_name>[, ...]
```

</details>

<details><summary>SCHEMA</summary>

```sql
SCHEMA <schema_name>[, ...]
```

</details>

<details><summary>TABLESPACE</summary>

```sql
TABLESPACE <tablespace_name>[, ...]
```

#### パラメータ

<details><summary>tablespace_name</summary>
</details>

</details>

</details>

<details><summary>FROM</summary>

```sql
FROM {[GROUP] <role_name> | PUBLIC | CURRENT_USER | SESSION_USER}[, ...]
```

#### パラメータ

<details><summary>role_name</summary>
</details>

#### 句

<details><summary>GROUP</summary>

```sql
GROUP
```

</details>

<details><summary>PUBLIC</summary>

```sql
PUBLIC
```
</details>

<details><summary>CURRENT_USER</summary>

```sql
CURRENT_USER
```

</details>

<details><summary>SESSION_USER</summary>

```sql
SESSION_USER
```

</details>

</details>

<details><summary>CASCADE</summary>

```sql
CASCADE
```

</details>

<details><summary>RESTRICT</summary>

```sql
RESTRICT
```

</details>

<details><summary>ADMIN OPTION FOR</summary>

```sql
ADMIN OPTION FOR
```

</details>

<details><summary>GRANT OPTION FOR</summary>

```sql
GRANT OPTION FOR
```

</details>
