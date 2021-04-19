# ALTER DATABASE

データベースを変更します。

```sql
ALTER DATABASE <name> [WITH]
```

## パラメータ

<details><summary>name</summary>

変更するデータベースの名前

</details>

## 句

<details><summary>WITH</summary>

変更するオプションを指定します。

```sql
[WITH] {RENAME TO | OWNER TO | SET | RESET}
```

### 句

<details><summary>RENAME TO</summary>

データベースの名前を変更する。

```sql
RENAME TO <new_name>
```

</details>

<details><summary>OWNER TO</summary>

所有者を変更する。

```sql
OWNER TO {<new_owner> | CURRENT_USER | SESSION_USER}
```

</details>

<details><summary>SET</summary>

データベースのパラメータをセットします。

```sql
SET {
        <configuration_parameters> {TO | =} {<value> | DEFAULT}
        | TABLESPACE <new_tablespace>
}
```

</details>

<details><summary>RESET</summary>

システムのデフォルト値を設定する。

```sql
RESET {<configuration_parameters> | ALL}
```

</details>

</details>
