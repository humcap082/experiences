# CREATE SEQUENCE

```sql
CREATE [TEMP] SEQUENCE [IF NOT EXISTS] <name>
    [AS] [INCREMENT] [MINVALUE] [MAXVALUE] [START]
    [CACHE] [CYCLE] [OWNED BY]
```

### パラメータ

<details><summary>name</summary>

作成するシーケンス名。

</details>

### 句

<details><summary>TEMP</summary>

```sql
TEMP
```

</details>

<details><summary>IF NOT EXISTS</summary>

```sql
IF NOT EXISTS
```

</details>

<details><summary>AS</summary>

```sql
AS <data_type>
```

### パラメータ

<details><summary>data_type</summary>
</details>

</details>

<details><summary>INCREMENT</summary>

```sql
INCREMENT [BY] <increment>
```

### パラメータ

<details><summary>increment</summary>
</details>

### 句

<details><summary>BY</summary>

```sql
BY
```

</details>

</details>

<details><summary>MINVALUE</summary>

```sql
{MINVALUE <min_value> | NO MINVALUE}
```

### パラメータ

<details><summary>min_value</summary>
</details>

### 句

<details><summary>NO MINVALUE</summary>
</details>

</details>

<details><summary>MAXVALUE</summary>

```sql
{MAXVALUE <max_value> | NO MAXVALUE}
```

### パラメータ

<details><summary>max_value</summary>
</details>

### 句

<details><summary>NO MAXVALUE</summary>
</details>

</details>

<details><summary>START</summary>

```sql
START [WITH] <start>
```

### パラメータ

<details><summary>start</summary>
</details>

### 句

<details><summary>WITH</summary>
</details>

</details>

<details><summary>CACHE</summary>

```sql
CACHE <cache>
```

### パラメータ

<details><summary>cache</summary>
</details>

</details>

<details><summary>CYCLE</summary>

```sql
[NO] CYCLE
```

### 句

<details><summary>NO</summary>

```sql
NO
```

</details>

</details>

<details><summary>OWNED BY</summary>

```sql
OWNED BY {<table_name>.<column_name> | NONE}
```

### パラメータ

<details><summary>table_name</summary>
</details>

<details><summary>column_name</summary>
</details>

### 句

<details><summary>NONE</summary>

```sql
NONE
```

</details>

</details>
