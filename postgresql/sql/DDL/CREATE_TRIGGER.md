# CREATE TRIGGER

トリガを定義する。

```sql
CREATE [CONSTRAINT] TRIGGER <name> {BEFORE | AFTER | INSTEAD OF}
    {INSERT | UPDATE | DELETE | TRUNCATE}[OR ...]
    ON
    [FROM]
    [DEFERRABLE]
    [INITIALLY]
    [REFERENCING]
    [FOR]
    [WHEN]
    EXECUTE FUNCTION
```

## パラメータ

<details><summary>name</summary>
</details>

## 句

<details><summary>CONSTRAINT</summary>

```sql
CONSTRAINT
```

</details>

<details><summary>BEFORE</summary>

```sql
BEFORE
```

</details>

<details><summary>AFTER</summary>

```sql
AFTER
```

</details>

<details><summary>INSTEAD OF</summary>

```sql
INSTEAD OF
```

</details>

<details><summary>ON</summary>

```sql
ON <table_name>
```

### パラメータ

<details><summary>table_name</summary>
</details>

</details>

<details><summary>FROM</summary>

```sql
FROM <referenced_table_name>
```

### パラメータ

<details><summary>referenced_table_name</summary>
</details>

</details>

<details><summary>DEFERRABLE</summary>

```sql
[NOT] DEFERRABLE
```

### 句

<details><summary>NOT</summary>
</details>

</details>

<details><summary>INITIALLY</summary>

```sql
INITIALLY {IMMEDIATE | DEFERRED}
```

### 句

<details><summary>IMMEDIATE</summary>

```sql
IMMEDIATE
```

</details>

<details><summary>DEFERRED</summary>

```sql
DEFERRED
```

</details>

</details>

<details><summary>REFERENCING</summary>

```sql
REFERENCING {{OLD | NEW} TABLE}
```

### 句

<details><summary>OLD</summary>

```sql
OLD
```

</details>

<details><summary>NEW</summary>

```sql
NEW
```

</details>

<details><summary>TABLE</summary>

```sql
TABLE [AS] <transition_relation_name>
```

#### パラメータ

<details><summary>transition_relation_name</summary>
</details>

#### 句

<details><summary>AS</summary>

```sql
AS
```

</details>

</details>

</details>

<details><summary>FOR</summary>

```sql
FOR [EACH] {ROW | STATEMENT}
```

### 句

<details><summary>EACH</summary>

```sql
EACH
```

</details>

<details><summary>ROW</summary>

```sql
ROW
```

</details>

<details><summary>STATEMENT</summary>

```sql
STATEMENT
```

</details>

</details>

<details><summary>WHEN</summary>

```sql
WHEN (<condition>)
```

### パラメータ

<details><summary>condition</summary>
</details>

</details>

<details><summary>EXECUTE FUNCTION</summary>

```sql
EXECUTE FUNCTION <function_name> (<arguments>)
```

### パラメータ

<details><summary>function_name</summary>
</details>

<details><summary>arguments</summary>
</details>

</details>
