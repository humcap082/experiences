# CREATE TYPE

```sql
CREATE TYPE <name> [
    AS
    | INPUT, OUTPUT[, RECEIVE][, SEND][, TYPMOD_IN][, TYPMOD_OUT]
        [, ANALYZE][, INTERNALLENGTH][, PASSEDBYVALUE][, ALIGNMENT]
        [, STORAGE][, LIKE][, CATEGORY][, PREFERRED][, DEFAULT]
        [, ELEMENT][, DELEMITER][, COLLATABLE]
]
```

## パラメータ

<details><summary>name</summary>
</details>

## 句

<details><summary>AS</summary>

```sql
AS {
    ([<attribute_name> <data_type> [COLLATE]][, ...])
    | ENUM
    | RANGE
}
```

### パラメータ

<details><summary>attribute_name</summary>
</details>

<details><summary>data_type</summary>
</details>

### 句

<details><summary>COLLATE</summary>

```sql
COLLATE <collation>
```

#### パラメータ

<details><summary>collation</summary>
</details>

</details>

<details><summary>ENUM</summary>

```sql
ENUM (['<label>'][, ...])
```

#### パラメータ

<details><summary>label</summary>
</details>

</details>

<details><summary>RANGE</summary>

```sql
RANGE (
    SUBTYPE,
    [, SUBTYPE_OPCLASS]
    [, COLLATION]
    [, CANONICAL]
    [, SUBTYPE_DIFF]
)
```

#### 句

<details><summary>SUBTYPE</summary>

```sql
SUBTYPE = <subtype>
```

##### パラメータ

<details><summary>subtype</summary>
</details>

</details>

<details><summary>SUBTYPE_OPCLASS</summary>

```sql
SUBTYPE_OPCLASS = <subtype_operator_class>
```

##### パラメータ

<details><summary>subtype_operator_class</summary>
</details>

</details>

<details><summary>COLLATION</summary>

```sql
COLLATION = <collation>
```

##### パラメータ

<details><summary>collation</summary>
</details>

</details>

<details><summary>CANONICAL</summary>

```sql
CANONICAL = <canonical_function>
```

##### パラメータ

<details><summary>canonical_function</summary>
</details>

</details>

<details><summary>SUBTYPE_DIFF</summary>

```sql
SUBTYPE_DIFF = <subtype_diff_function>
```

### パラメータ

<details><summary>subtype_diff_function</summary>
</details>

</details>

</details>

</details>

<details><summary>INPUT</summary>

```sql
INPUT = <input_function>
```

### パラメータ

<details><summary>input_function</summary>
</details>

</details>

<details><summary>OUTPUT</summary>

```sql
OUTPUT = <output_function>
```

### パラメータ

<details><summary>output_function</summary>
</details>

</details>

<details><summary>RECEIVE</summary>

```sql
RECEIVE = <receive_function>
```

### パラメータ

<details><summary>receive-function</summary>
</details>

</details>

<details><summary>SEND</summary>

```sql
SEND = <send_function>
```

### パラメータ

<details><summary>send_function</summary>
</details>

</details>

<details><summary>TYPMOD_IN</summary>

```sql
TYPMOD_IN = <type_modifier_input_function>
```

### パラメータ

<details><summary>type_modifier_input_function</summary>
</details>

</details>

<details><summary>TYPMOD_OUT</summary>

```sql
TYPMOD_OUT = <type_modifier_output_function>
```

### パラメータ

<details><summary>type_modifier_output_function</summary>
</details>

</details>

<details><summary>ANALYZE</summary>

```sql
ANALYZE = <analyze_function>
```

### パラメータ

<details><summary>analyze_function</summary>
</details>

</details>

<details><summary>INTERNALLENGTH</summary>

```sql
INTERNALLENGTH = {<internallength> | VARIABLE}
```

### パラメータ

<details><summary>internallength</summary>
</details>

### 句

<details><summary>VARIABLE</summary>
</details>

</details>

<details><summary>PASSEDBYVALUE</summary>

```sql
PASSEDBYVALUE
```

</details>

<details><summary>ALIGNMENT</summary>

```sql
ALIGNMENT = <alignment>
```

### パラメータ

<details><summary>alignment</summary>
</details>

</details>

<details><summary>STORAGE</summary>

```sql
STORAGE = <storage>
```

### パラメータ

<details><summary>storage</summary>
</details>

</details>

<details><summary>LIKE</summary>

```sql
LIKE = <like_type>
```

### パラメータ

<details><summary>like_type</summary>
</details>

</details>

<details><summary>CATEGORY</summary>

```sql
CATEGORY = <category>
```

### パラメータ

<details><summary>category</summary>
</details>

</details>

<details><summary>PREFERRED</summary>

```sql
PREFERRED = <preferred>
```

### パラメータ

<details><summary>preferred</summary>
</details>

</details>

<details><summary>DEFAULT</summary>

```sql
DEFAULT = <default>
```

### パラメータ

<details><summary>default</summary>
</details>

</details>

<details><summary>ELEMENT</summary>

```sql
ELEMENT = <element>
```

### パラメータ

<details><summary>element</summary>
</details>

</details>

<details><summary>DELIMITER</summary>

```sql
DELIMITER = <delimiter>
```

### パラメータ

<details><summary>delimiter</summary>
</details>

</details>

<details><summary>COLLATABLE</summary>

```sql
COLLATABLE = <collatable>
```

### パラメータ

<details><summary>collatable</summary>
</details>

</details>
