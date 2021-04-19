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
        | VALIDATE
        | DISABLE
        | ENABLE
        | FORCE
        | CLUSTER ON
        | RESET
        | INHERIT
        | OF
        | OWNER TO
        | REPLICA IDENTITY
    }
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

</details>

<details><summary>ATTACH PARTITION</summary>
</details>

<details><summary>DETACH PARTITION</summary>
</details>

<details><summary>ADD</summary>
</details>

<details><summary>DROP</summary>
</details>

<details><summary>ALTER</summary>
</details>

<details><summary>VALIDATE</summary>
</details>

<details><summary>DISABLE</summary>
</details>

<details><summary>ENABLE</summary>
</details>

<details><summary>FORCE</summary>
</details>

<details><summary>CLUSTER ON</summary>
</details>

<details><summary>RESET</summary>
</details>

<details><summary>INHERIT</summary>
</details>

<details><summary>OF</summary>
</details>

<details><summary>OWNER TO</summary>
</details>

<details><summary>REPLICA IDENTITY</summary>
</details>

<details><summary>ALL IN TABLESPACE</summary>
</details>
