# CREATE_VIEW

ビューを作成する。

```sql
CREATE [OR REPLACE] [RECURSIVE] VIEW <name> [(<column_name>[, ...)]
    [WITH] AS [WITH CHECK OPTION]
```

## パラメータ

<details><summary>name</summary>

作成するビューの名前

</details>

<details><summary>column_name</summary>
</details>

## 句

<details><summary>OR REPLACE</summary>

```sql
OR REPLACE
```

</details>

<details><summary>RECURSIVE</summary>

```sql
RECURSIVE
```

</details>

<details><summary>WITH</summary>

```sql
WITH ({<query_option_name>[= <view_option_value>]}[, ...])
```

### パラメータ

<details><summary>query_option_name</summary>
</details>

<details><summary>view_option_value</summary>
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

<details><summary>WITH CHECK OPTION</summary>

```sql
WITH [CASCADED | LOCAL] CHECK OPTION
```

### 句

<details><summary>CASCADED</summary>
</details>

<details><summary>LOCAL</summary>
</details>

</details>
