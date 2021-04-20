# CREATE INDEX

インデックスを定義する。

```sql
CREATE [UNIQUE] INDEX [CONCURRENTLY] [[IF NOT EXISTS] <name>]
    ON [INCLUDE] [WITH] [TABLESPACE] [WHERE]
```

## パラメータ

<details><summary>name</summary>
</details>

## 句

<details><summary>UNIQUE</summary>

```sql
UNIQUE
```

</details>

<details><summary>CONCURRENTLY</summary>

```sql
CONCURRENTLY
```

</details>

<details><summary>IF NOT EXISTS</summary>

```sql
IF NOT EIXISTS
```

</details>

<details><summary>ON</summary>

```sql
ON [ONLY] <table_name> [USING] ({
    {<column_name> | <expression>} [COLLATE] [<opclass>]
        [ASC | DESC] [NULLS]
}[,...])
```

### パラメータ

<details><summary>table_name</summary>
</details>

<details><summary>column_name</summary>
</details>

<details><summary>opclass</summary>
</details>

### 句

<details><summary>ONLY</summary>

```sql
ONLY
```

</details>

<details><summary>USING</summary>

```sql
USING
```

</details>

<details><summary>COLLATE</summary>

```sql
COLLATE <collation>
```

</details>

<details><summary>ASC</summary>

```sql
ASC
```

</details>

<details><summary>DESC</summary>

```sql
DESC
```

</details>

<details><summary>NULLS</summary>

```sql
NULLS {FIRST | LAST}
```

#### 句

<details><summary>FIRST</summary>

```sql
FIRST
```

</details>

<details><summary>LAST</summary>

```sql
LAST
```

</details>

</details>

</details>

<details><summary>INCLUDE</summary>

```sql
INCLUDE (<column_name[, ...]>)
```

### パラメータ

<details><summary>column_name</summary>
</details>

</details>

<details><summary>WITH</summary>

```sql
WITH ({<storage_parameter>[= <value>]}[, ...])
```

</details>

<details><summary>TABLESPACE</summary>

```sql
TABLESPACE <tablespace_name>
```

### パラメータ

<details><summary>tablespace_name</summary>
</details>

</details>

<details><summary>WHERE</summary>

```sql
WHERE <predicate>
```

### パラメータ

<details><summary>predicate</summary>
</details>

</details>
