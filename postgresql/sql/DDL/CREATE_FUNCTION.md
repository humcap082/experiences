# CREATE FUNCTION

```sql
CREATE [OR REPLACE] FUNCTION
    <name>([[<arg_mode>] [arg_name] arg_type [DEFAULT]][,...])
    [RETURNS] [AS] [LANGUAGE] [TRANSFORM] [WINDOW]
        [IMMUTABLE] [STABLE] [VOLATILE] [LEAKPROOF]
        [CALLED ON NULL INPUT] [RETURNS NULL ON NULL INPUT]
        [STRICT] [SECURITY] [PARALLEL] [COST] [ROWS] [SUPPORT]
        [SET]
```

## パラメータ

<details><summary>arg_mode</summary>
</details>

<details><summary>arg_name</summary>
</details>

<details><summary>arg_type</summary>
</details>

## 句

<details><summary>OR REPLACE</summary>

```sql
OR REPLACE
```

</details>

<details><summary>DEFAULT</summary>

```sql
{DEFAULT | =} <default_expr>
```

</details>

<details><summary>RETURNS</summary>

```sql
RETURNS {<ret_type> | TABLE ({<column_name> <column_type>}[, ...])}
```

</details>

<details><summary>AS</summary>

```sql
AS {'<definition>' | '<obj_file>', '<link_symbol>'}
```

### パラメータ

<details><summary>definition</summary>
</details>

<details><summary>obj_file</summary>
</details>

<details><summary>link_symbol</summary>
</details>

</details>

<details><summary>LANGUAGE</summary>

```sql
LANGUAGE <lang_name>
```

### パラメータ

<details><summary>lang_name</summary>
</details>

</details>

<details><summary>TRANSFORM</summary>

```sql
TRANSFORM {FOR TYPE}[, ...]
```

### 句

<details><summary>FOR TYPE</summary>

```sql
FOR TYPE <type_name>
```

</details>

</details>

<details><summary>WINDOW</summary>

```sql
WINDOW
```

</details>

<details><summary>IMMUTABLE</summary>

```sql
IMMUTABLE
```

</details>

<details><summary>STABLE</summary>

```sql
STABLE
```

</details>

<details><summary>VOLATILE</summary>

```sql
VOLATILE
```

</details>

<details><summary>LEAKPROOF</summary>

```sql
[NOT] LEAKPROOF
```

### 句

<details><summary>NOT</summary>

```sql
NOT
```

</details>

</details>

<details><summary>CALLED ON NULL INPUT</summary>

```sql
CALLED ON NULL INPUT
```

</details>

<details><summary>RETURNS NULL ON NULL INPUT</summary>

```sql
RETURNS NULL ON NULL INPUT
```

</details>

<details><summary>STRICT</summary>

```sql
STRICT
```

</details>

<details><summary>SECURITY</summary>

```sql
SECURITY [EXTERNAL] {INVOKER | DEFINER}
```

</details>

<details><summary>PARALLEL</summary>

```sql
PARALLEL {UNSAFE | RESTRICTED | SAFE}
```

### 句

<details><summary>UNSAFE</summary>

```sql
UNSAFE
```

</details>

<details><summary>RESTRICTED</summary>

```sql
RESTRICTED
```

</details>

<details><summary>SAFE</summary>

```sql
SAFE
```

</details>

</details>

<details><summary>COST</summary>

```sql
COST <execution_cost>
```

### パラメータ

<details><summary>execution_cost</summary>
</details>

</details>

<details><summary>ROWS</summary>

```sql
ROWS <result_rows>
```

### パラメータ

<details><summary>result_rows</summary>
</details>

</details>

<details><summary>SUPPORT</summary>

```sql
SUPPORT <support_function>
```

### パラメータ

<details><summary>support_function</summary>
</details>

</details>

<details><summary>SET</summary>

```sql
SET <configuraton_parameter> {TO | = <value> | FROM CURRENT}
```

### パラメータ

<details><summary>configuration_parameter</summary>
</details>

<details><summary>value</summary>
</details>

### 句

<details><summary>TO</summary>

```sql
TO <value>
```

#### パラメータ

<details><summary>value</summary>
</details>

</details>

<details><summary>FROM CURRENT</summary>

```sql
FROM CURRENT
```

</details>

</details>
