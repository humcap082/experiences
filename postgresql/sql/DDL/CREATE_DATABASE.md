# CREATE DATABASE

データベースを作成する。

実行するにはスーパーユーザー、もしくは`CREATEDB`という特別な権限をもつ

ユーザーである必要があります。デフォルトでは`template1`を複製することによって

作成されます。トランザクションブロック内では実行できません。

```sql
CREATE DATABASE <name> [WITH]
```

## パラメータ

<details><summary>name</summary>

作成するデータベース名。

</details>

## 句

<details><summary>WITH</summary>

`WITH`は省略可能です。

```sql
[WITH]
    [OWNER]
    [TEMPLATE]
    [ENCODING]
    [LC_COLLATE]
    [LC_CTYPE]
    [TABLESPACE]
    [ALLOW_CONNECTIONS]
    [CONNECTION LIMIT]
    [IS_TEMPLATE]
```

<details><summary>OWNER</summary>

所有者を指定する。

```sql
OWNER [=] <user_name>
```

</details>

<details><summary>TEMPLATE</summary>

新しいデータベースの作成元となるテンプレートの名前。

```sql
TEMPLATE [=] <template>
```

</details>

<details><summary>ENCODING</summary>

文字コード

```sql
ENCODING [=] <encoding>
```

</details>

<details><summary>lC_COLLATE</summary>

 照合順

```sql
LC_COLLATE [=] <lc_collate>
```

</details>

<details><summary>LC_CTYPE</summary>

文字クラス

```sql
LC_CTYPE [=] <lc_ctype>
```

</details>

<details><summary>TABLESPACE</summary>

 デフォルトのテーブルの空間名。

```sql
TABLESPACE [=] <tablespace_name>
```

</details>

<details><summary>ALLOW_CONNECTIONS</summary>

`false`のとき誰も節zくすることができません。

```sql
ALLOW_CONNECTIONS [=] <allow_conn>
```

</details>

<details><summary>CONNECTION LIMIT</summary>

同時接続数の条件。`-1`は無制限を意味します。

```sql
CONNECTION LIMIt [=] <conn_limit>
```

</details>

<details><summary>IS_TEMPLATE</summary>

`true`の場合、テンプレートデータベースとして使用でき、

どのユーザーでもコピーが可能です。

`false`の場合は、スーパーユーザーもしくはデータベースの所有者のみが

コピーできます。

```sql
IS_TEMPLATE [=] <is_template>
```

</details>

</details>
