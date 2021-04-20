# CREATE MATERIALIZED VIEW

マテリアライズドビューを定義する。

```sql
CREATE MATERIALIZED VIEW [IF NOT EXISTS]
    <table_name> [(<column_name>[, ...])]
    [USING]
    [WITH]
    [TABLESPACE]
    AS
    [WITH DATA]
```

## パラメータ

<details><summary>table_name</summary>
</details>

<details><summary>column_name</summary>
</details>

## 句

<details><summary>IF NOT EXISTS</summary>

```sql
IF NOT EXISTS
```

</details>

<details><summary>USING</summary>

```sql
USING <method>
```

### パラメータ

<details><summary>method</summary>
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

<details><summary>AS</summary>

```sql
AS <query>
```

### パラメータ

<details><summary>query</summary>

</details>

</details>

<details><summary>WITH DATA</summary>

```sql
WITH [NO] DATA
```

### 句

<details><summary>NO</summary>

```sql
NO
```

</details>

</details>
