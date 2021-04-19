# ALTER ROLE

データベースロールを変更する。

```sql
ALTER ROLE {<role_name> | CURRENT_USER | SESSION_USER | ALL}
    {
        [WITH]
        [SUPERUSER | NOSUPERUSER]
        [CREATEDB | [NOCREATEDB]
        [CREATEROLE | NOCREATEROLE]
        [INHERIT | NOINHERIT]
        [LOGIN | NOLOGIN]
        [REPLICATION | NOREPLICATION]
        [BYPASSRLS | NOBYPASSRLS]
        [CONNECTION LIMIT]
        [PASSWORD]
        [VALID UNTIL]
        [IN ROLE]
        [ROLE]
        [ADMIN]
        | RENAME TO
        | [IN DATABASE] {SET | RESET}
    }
```

### 句

<details><summary>WITH</summary>

特に意味はないく、省略が可能。

```sql
WITH
```

</details>

<details><summary>SUPERUSER</summary>

 スーパーユーザーに設定

 ```sql
 SUPERUSER
 ```

</details>

<details><summary>NOSUPERUSER</summary>

スーパーユーザーではない、デフォルトです。

```sql
NOSUPERUSER
```

</details>

<details><summary>CREATEDB</summary>

データベースを作成する権限を定義する。

```sql
CREATEDB
```

</details>

<details><summary>NOCREATEDB</summary>

データベースを作成する権限をもたない。デフォルトです。

```sql
NOCREATEDB
```

</details>

<details><summary>CREATEROLE</summary>

新しいロールを作成することができる権限。　

```sql
CREATEROLE
```

</details>

<details><summary>NOCREATEROLE</summary>

新しいロールを作成することができない。デフォルトです。

```sql
NOCREATEROLE
```

</details>

<details><summary>INHERIT</summary>

作成したユーザーのロールを継承する。デフォルトです。

```sql
INHERIT
```

</details>

<details><summary>NOINHERIT</summary>

作成したユーザーのロールを継承しない。

```sql
NOINHERIT
```

</details>

<details><summary>LOGIN</summary>

 ログインが可能。すなわちセッションの認証に

 使用できる。

```sql
LOGIN
```

</details>

<details><summary>NOLOGIN</summary>

ログインが不可能。セッションの認証に使用できない。

```sql
NOLOGIN
```

</details>

<details><summary>REPLICATION</summary>

レプリケーションモードのサーバーの接続、レプリケーションスロットの

作成、削除ができる。

```sql
REPLICATION
```

</details>

<details><summary>NOREPLICATION</summary>

レプリケーションモードのサーバーの接続、レプリケーションスロットの

作成、削除ができない。デフォルトです。

```sql
NOREPLICATION
```

</details>

<details><summary>BYPASSRLS</summary>

セキュリティポリシー(RLS)に準じる。

```sql
BYPASSRLS
```

</details>

<details><summary>NOBYPASSRLS</summary>

セキュリティポリシー(RLS)を削除する。

```sql
NOBYPASSRLS
```

</details>

<details><summary>CONNECTION LIMIT</summary>

ロールが確立できる最大同時接続数を指定する。

```sql
CONNECTION LIMIT <conn_limit>
```

## パラメータ

<details><summary>conn_limit</summary>

最大同時接続数。-1で無制限でこれがデフォルトです。

</details>

</details>

<details><summary>PASSWORD</summary>

パスワードを設定する。

```sql
PASSWORD {'<password>' | NULL}
```

</details>

<details><summary>VALID UNTIL</summary>

パスワードの有効期限を指定する。

```sql
VALID UNTIL `<timestamp>`
```

</details>

<details><summary>IN ROLE</summary>

新しく作成するロールを新規にメンバ通して追加する既存のロールを

一つ以上追加する。

```sql
IN ROLE <role_name>[, ...]
```

</details>

<details><summary>ROLE</summary>

新しく作成するロールのメンバとして自動的に追加する既存のメンバを設定する。

```sql
ROLE <role_name>[, ...]
```

</details>

<details><summary>ADMIN</summary>

`ROLE`と似ていますが、`WITH ADMIN OPTION`が付与されるため

ロールのメンバ資格を他社に与える権利を与える。

```sql
ADMIN
```

</details>

<details><summary>IN DATABASE</summary>

データーベースを指定する。

```sql
IN DATABASE <database_name>
```

</details>

<details><summary>RENAME TO</summary>

ロールの名前を変更する。

```sql
RENAME TO <new_name>
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
