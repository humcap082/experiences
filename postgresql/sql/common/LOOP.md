# LOOP

```sql
[\<\<<label>\>\>]
[WHILE | FOR] LOOP
    [<statement>;]
    [, ...]
    [EXIT]
END LOOP [<label>]
```

## パラメータ

<details><summary>statement</summary>
</details>

<details><summary>label</summary>
</details>

## 句

<details><summary>WHILE</summary>

```sql
WHILE [boolean_expression]
```

### パラメータ

<details><summary>boolean_expression</summary>
</details>

</details>

<details><summary>FOR</summary>

```sql
FOR <name> IN [BY]
```

### パラメータ

<details><summary>name</summary>
</details>

### 句

<details><summary>IN</summary>

```sql
IN [REVERSE] {<expression>..<expression> | <query> | ARRAY}
```

#### パラメータ

<details><summary>expression</summary>
</details>

#### 句

<details><summary>REVERSE</summary>

```sql
REVERSE
```

</details>

<details><summary>ARRAY</summary>

```sql
ARRAY <expression>
```

</details>

</details>

<details><summary>BY</summary>

```sql
BY <expression>
```

#### パラメータ

<details><summary>expression</summary>
</details>

</details>

</details>

<details><summary>EXIT</summary>

```sql
EXIT [<label>] [WHEN]
```

### 句

<details><summary>WHEN</summary>

```sql
WHEN [<boolean_expression>]
```

</details>

</details>
