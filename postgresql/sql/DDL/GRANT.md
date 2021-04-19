# GRANT

アクセス権限を定義する。

```sql
GRANT {
    {
        [SELECT] [, INSERT] [, UPDATE] [, DELETE]
            [, TRUNCATE] [, REFERENCES] [, TRIGGER]
            [, USAGE] [, CREATE] [, CONNECT] [, TEMP]
            [, EXECUTE]
        | ALL
    } ON
    | <role_name>
} TO [WITH GRANT OPTION] [WITH ADMIN OPTION] [GRANTED BY]
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
}
```

### 句

<details><summary>ALL</summary>

```sql
ALL {TABLES | SEQUENCES | FUNCTIONS | ROUTINES} IN SCHEMA <schema_name>[, ...]
```

</details>

<details><summary>SEQUENCE</summary>

```sql
SEQUENCE <sequence_name>[, ...]
```

</details>

</details>

<details><summary>TO</summary>

```sql
TO {<role_name> | PUBLIC | CURRENT_USER | SESSION_USER}[, ...]
```

</details>

<details><summary>WITH GRANT OPTION</summary>

```sql
WITH GRANT OPTION
```

</details>

<details><summary>WITH ADMIN OPTION</summary>

```sql
WITH ADMIN OPTION
```

</details>

<details><summary>GRANTED BY</summary>

```sql
GRANTED BY <role_specification>
```

</details>
